<template>
	<div>
		<div class="hot-title">周末去哪儿玩</div>
		<ul>
			<li class="item border-bottom" v-for="item of weekcommend" :key="item.id">
				<div class="item-img-wraper">
					<img class="item-img" :src="item.imgUrl" alt="">
				</div>
				<div class="item-info">
					<p class="item-title">{{item.title}}</p>
					<p class="item-desc">{{item.desc}}</p>
				</div>
			</li>
		</ul>
	</div>
</template>
<script>
	export default {
		name : "weekcommend",
		props:{
			weekcommend:Array
		}
	}
</script>
<style lang="stylus" scoped>
	.hot-title
	 margin-top:.2rem
	 line-height:.8rem
	 background:#e3e4e5
	 text-indent:.2rem
	.item-img-wraper
	  padding-bottom:33.9%
	  overfllow:hidden
	  height:0
	  .item-img
	   width:100%
	   height:2.5rem
	 .item-info
	  flex:1
	  padding:.1rem
	  .item-title
	   line-height:.54rem
	   font-size:.32rem
	  .item-desc
	   line-height:.4rem
	   color:#ccc
</style>