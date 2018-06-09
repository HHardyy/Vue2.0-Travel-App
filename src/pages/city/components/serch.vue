<template>
	<div>
		<div class="serch">
			<input type="text" v-model="keyword" class="SerchInput" placeholder="请输入城市或拼音">
		</div>
		<div class="serch-content" ref="serch" v-show="keyword">
			<ul>
				<li 
				v-for="item of list" 
				:key="item.id"
				@click="handelCheckHotcity(item.name)"
				class="serch-item border-bottom"
				>{{item.name}}</li>
				<li class="serch-item border-bottom no-data" v-show="hasNodata">
					没有找到匹配项
				</li>
			</ul>
		</div>
	</div>	
</template>
<script>
import bscroll from 'better-scroll'
	export default {
		name:"serch",
		props:{
			cities:Object
		},
		data(){
			return {
				keyword:'',
				list:[],
				timer:null
			}
		},
		methods:{
			handelCheckHotcity(city){
				this.$store.commit('changeCity',city)
				this.$router.push('/')
			}
		},
		watch:{
			keyword(){
				if (this.timer) {
					clearTimeout(this.timer)
				}
				if (!this.keyword) {
					this.list=[]
					return
				}
				this.timer=setTimeout(()=>{
					const result=[]
					for(let i in this.cities){
						this.cities[i].forEach((value) => {
							if(value.spell.indexOf(this.keyword) > -1||value.name.indexOf(this.keyword) > -1){
								result.push(value)
							}
						})
					}
					this.list=result
				},100)
			}
		},
		mounted(){
			this.bscroll=new bscroll(this.$refs.serch)
		},
		computed:{
			hasNodata(){
				return !this.list.length
			}
		}
	}
</script>
<style lang="stylus" scoped>
    @import '~@/assets/styles/varyble.styl'
	.serch
	 height:.72rem
	 padding:0 0.1rem
	 background:$bgColor
	 box-sizing:border-box
	 .SerchInput
	  border-radius:.06rem
	  height:.62rem
	  line-height:.62rem
	  width:97%
	  text-align:center
	  padding:0 .1rem
	.serch-content
	 overflow:hidden
	 position:absolute
	 top:1.58rem
	 left:0
	 bottom:0
	 right:0
	 z-index:1
	 .serch-item
	  line-height:.62rem
	  padding-left:.2rem
	  color:#fff
	  background:#acacac
	 .no-data
	  padding:.2rem 0
	  text-align:center
</style>