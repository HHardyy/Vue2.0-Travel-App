<template>
	<div class="header">
		<div class="header-left">
      <div class="iconfont ba-icon">&#xe624;</div>
    </div>
    <div class="header-input"><span class="iconfont">&#xe632;</span>请输入城市 / 景点 / 游玩主题</div>
    <router-link to="/city">
      <div class="header-right">
        {{this.$store.state.city}}
        <span class="iconfont up-icon">&#xe62d;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
	export default {
		name : 'Header'
	}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varyble.styl'
.header
  display:flex
  height:$header-height
  background:$bgColor
  line-height:$header-height
  color:#fff
  .header-left
    width:.64rem
    text-align:center
    float:left
    .ba-icon
      font-size:.4rem
  .header-input
    flex:1
    padding-left:.2rem
    border-radius:.1rem
    height:.64rem
    line-height:.64rem
    background:#ffe1e1
    margin-top:.12rem
    margin-left:.2rem
    color:#c6c6c6
  .header-right
    width:1.24rem
    float:right
    color:#fff
    font-size:.3rem
    text-align:center
    .up-icon
     margin-left:.0.4rem
     font-size:.2rem
</style>