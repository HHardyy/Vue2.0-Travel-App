<template>
	<div class="gallary" @click="handelGallaryClick">
		<div class="wrapper">
			<swiper :options="swiperOption">
				<swiper-slide
				v-for="(item,index) of imgs"
				:key="index"
				>
					<img class="gallary-img" :src="item" alt="">
				</swiper-slide>
				<div class="swiper-pagination"  slot="pagination"></div>
			</swiper>
		</div>
	</div>
</template>
<script>
	export default {
		name:'gallary',
		props:{
			imgs:{
				type:Array
			}
		},
		data(){
			return {
				swiperOption:{
					pagination:'.swiper-pagination',
					paginationType:'fraction',
					observeParents:true,
					observer:true
				}
			}
		},
		methods:{
			handelGallaryClick(){
				this.$emit('close')
			}
		}
	}
</script>
<style lang='stylus' scope>
 .gallary
  display:flex
  flex-direction:column
  justify-content:center
  position:fixed
  top:0
  left:0
  bottom:0
  right:0
  background:#262626
  z-index:99
  .wrapper
   width:100%
   height:0
   padding-bottom:100%
   .swiper-container
    overflow:inherit
   .gallary-img
    width:100%
    height:6rem
   .swiper-pagination
    bottom:-2rem
    color:#fff
</style>