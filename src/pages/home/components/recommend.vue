<template>
	<div>
		<div class="hot-title">推荐信息</div>
		<ul>
			<router-link
			tag="li"
			class="item border-bottom" 
			v-for="item of recommend" 
			:key="item.id"
			:to="'/detail/'+item.id"
			>
				<img class="item-img" :src="item.imgUrl" alt="">
				<div class="item-info">
					<p class="item-title">{{item.title}}</p>
					<p class="item-desc">{{item.desc}}</p>
					<button class="item-button">查看详情</button>
				</div>
			</router-link>
		</ul>
	</div>
</template>
<script>
	export default {
		name : "recommend",
		props:{
			recommend:Array
		}
	}
</script>
<style lang="stylus" scoped>
	.hot-title
	 margin-top:.2rem
	 line-height:.8rem
	 background:#e3e4e5
	 text-indent:.2rem
	.border-bottom
	 border-bottom:1px solid #a4a7aa
	.item
	 display:flex
	 height:1.9rem
	 overfllow:hidden
	 .item-img
	  padding:.1rem
	  height:1.7rem
	  width:1.7rem
	 .item-info
	  flex:1
	  padding:.1rem
	  .item-title
	   line-height:.54rem
	   font-size:.32rem
	  .item-desc
	   line-height:.4rem
	   color:#ccc
	  .item-button
	   padding:0 .2rem
	   margin-top:.16rem
	   background:#ff9300
	   border-radius:.06rem
	   color:#fff
	   line-height:.44rem
</style>