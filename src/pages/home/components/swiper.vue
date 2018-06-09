<template>
	<div class="wranpper">
		<swiper :options="swiperOption" v-if="showswiper">
			<!-- slides -->
			<swiper-slide v-for="item of list" :key="item.id">
				<img class="swiper-img" :src="item.imgUrl" alt="">
			</swiper-slide>
			<div class="swiper-pagination"  slot="pagination"></div>
		</swiper>
	</div>
</template>

<script>
	export default {
		name: "HomeSwiper",
		props:{
			list:Array
		},
		data(){
			return {
				swiperOption:{
					pagination:'.swiper-pagination',
					loop:true
				}
			}
		},
		computed:{
			showswiper(){
				return this.list.length
			}
		}
	}
</script>

<style lang="stylus" scoped>
     .wranpper
      width:100%
      overfllow:hidden
      height:46.25vw
	  .swiper-img
		width:100%
		height:3.53rem
</style>