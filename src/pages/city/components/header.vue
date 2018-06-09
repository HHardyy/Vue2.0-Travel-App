<template>
	<div class="header">
		城市选择
		<div>
			<router-link to='/'>
			<div class="iconfont back-icon">&#xe624;</div>
		    </router-link>
		</div>
	</div>
</template>
<script>
	export default {
		name:"cityHeader"
	}
</script>
<style lang="stylus" scoped>
   @import '~@/assets/styles/varyble.styl'
   .header
    overfllow:hidden
    text-align:center
    color:#fff
    font-size:.32rem
    background:$bgColor
    height:$header-height
    line-height:$header-height
    position:relative
    .back-icon
     width:.64rem
     color:#fff
     text-align:center
     font-size:.4rem
     position:absolute
     left:0
     top:0
</style>