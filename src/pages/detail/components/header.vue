<template>
  <div class="detail-header">
    <router-link 
    tag="div"
    to="/"
    class="header-abs"
    v-show="showAbs"
    >
    <span class="iconfont header-abs-icon">&#xe624;</span>
  </router-link>
  <div 
  class="header-fixed" 
  v-show="!showAbs" 
  :style="opacityStyle"
  >
    <router-link to='/'>
      <div class="iconfont header-fixed-back-icon">&#xe624;</div>
    </router-link>
    景点详情
  </div>
</div>
</template>

<script>
export default {
  name:'detail-header',
  data(){
    return {
      showAbs:true,
      opacityStyle:{
        opacity:0
      }
    }
  },
  methods:{
    handelScroll(){
      const scrooT=document.documentElement.scrollTop
      if (scrooT>60) {
        let opacity=scrooT/140
        opacity=opacity>1?1:opacity
        this.opacityStyle={opacity}
        this.showAbs=false
      }else{
        this.showAbs=true
      }
    }
  },
  activated(){
    window.addEventListener('scroll', this.handelScroll)
  },
  deactivated(){
    window.removeEventListener('scroll', this.handelScroll)
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varyble.styl'
 .header-abs
   position:absolute
   top:.2rem
   left:.2rem
   width:.8rem
   height:.8rem
   line-height:.8rem
   text-align:center
   border-radius:.4rem
   background:rgba(0,0,0,0.8)
   z-index:90
   .header-abs-icon
    font-size:.4rem
    color:#fff
  .header-fixed
    text-align:center
    color:#fff
    font-size:.32rem
    background:$bgColor
    height:$header-height
    line-height:$header-height
    position:fixed
    top:0
    left:0
    right:0
    z-index:90
    .header-fixed-back-icon
     width:.64rem
     color:#fff
     text-align:center
     font-size:.4rem
     position:absolute
     left:0
     top:0
     right:0
</style>
