<template>
	<div>
		<div class="banner" @click="handelBannerClick">
			<img class="banner-img" :src="bannerData.bannerImg" alt="">
			<div class="banner-info">
				<div class="banner-title">{{bannerData.sightName}}</div>
				<div class="banner-number"><span class="iconfont banner-icon">&#xe659;</span>{{gallaryImgLength}}</div>
			</div>
		</div>
		<fade-animation>
			<gallary :imgs="gallaryImgs" v-show="showGallary" @close="handelCloseGallary"></gallary>
		</fade-animation>
	</div>
</template>
<script>
import Gallary from '@/common/gallary/gallary'
import FadeAnimation from '@/common/fade/fade'
	export default {
		name:'banner',
		props:{
			bannerData:Object,
			gallaryImgs:Array
		},
		data(){
			return {
				showGallary:false
			}
		},
		methods:{
			handelBannerClick(){
				this.showGallary=true
			},
			handelCloseGallary(){
				this.showGallary=false
			}
		},
		components:{
			Gallary,
			FadeAnimation
		},
		computed:{
			gallaryImgLength(){
				return this.gallaryImgs.length
			}
		}
	}
</script>
<style lang="stylus" scoped>
	.banner
	 overflow:hidden
	 height:0
	 padding-bottom:55%
	 position:relative
	 .banner-img
	  width:100%
	 .banner-info
	  position:absolute
	  left:0
	  right:0
	  bottom:0
	  line-height:.6rem
	  display:flex
	  color:#fff
	  background:linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,0.8))
	  .banner-title
	   flex:1
	   font-size:.32rem
	   padding:0 .2rem
	  .banner-number
	   height:.32rem
	   margin-top:.14rem
	   padding:0 .4rem
	   line-height:.32rem
	   border-radius:.2rem
	   font-size:.24rem
	   background:rgba(0,0,0,0.8)
	   .banner-icon
	    font-size:.24rem
	    padding-right:.1rem
</style>