<template>
	<div class="icons">
		<swiper v-if="iconsLength">
			<swiper-slide v-for="(page,index) of pages" :key="index">
				<div 
				class="icon" 
				v-for="item of page" 
				:key="item.id">
					<div class="icon-img">
						<img class="icon-img-content" :src="item.imgUrl" alt="">
					</div>
					<p class="icon-sesc">{{item.desc}}</p>
				</div>
			</swiper-slide>
		</swiper>
	</div>
</template>

<script>
	export default{
		name:"icons",
		props:{
			iconlist:Array
		},
		computed: {
			iconsLength(){
				return this.iconlist.length
			},
			pages () {
				const pages = []
				this.iconlist.forEach((item, index) => {
					const page = Math.floor(index / 8)
					if (!pages[page]) {
						pages[page] = []
					}
					pages[page].push(item)
				})
				return pages
			}
		}
	}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varyble.styl'
  .icons >>> .swiper-container
   height:0
   padding-bottom:50%
  .icon
   width:25%
   padding-bottom:25%
   float:left
   height:0
   overfllow:hidden
   position:relative
   .icon-img
   	position:absolute
   	top:0
   	left:0
   	right:0
   	box-sizing:border-box
   	padding:.2rem
   	padding-bottom:.2rem
   	bottom:.44rem
   	.icon-img-content
   	 height:100%
   	 display:block
   	 margin:0 auto
   .icon-sesc
    position:absolute
   	left:0
   	right:0
   	bottom:0
   	height:.48rem
   	line-height:.48rem
   	color:$fontcolor
   	text-align:center
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
</style>