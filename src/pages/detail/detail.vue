<template>
	<div class="detail">
		<detail-header></detail-header>
		<detail-banner :bannerData="bannerData" :gallaryImgs="gallaryImgs"></detail-banner>
		<div class="content">
			<detail-list :list="list"></detail-list>
		</div>
	</div>
</template>
<script>
import DetailBanner from './components/banner.vue'
import DetailHeader from './components/header.vue'
import DetailList from './components/list.vue'
import axios from 'axios'
	export default {
		name:'detail',
		data(){
			return {
				list:[],
				bannerData:{},
				gallaryImgs:[]
			}
		},
		components:{
			DetailBanner,
			DetailHeader,
			DetailList
		},
		methods:{
			getDetailData(){
				axios.get('/api/detail.json',{
					params:{
						id:this.$route.params.id
					}
				})
				.then((res)=>{
					if (res.data) {
						const data=res.data
						this.list=data.data.categoryList
						this.bannerData=data.data
						this.gallaryImgs=data.data.gallaryImgs
					}
				})
				.catch((err)=>{
					console.log(err)
				})
			}
		},
		mounted(){
			this.getDetailData()
		}
	}
</script>
<style lang="stylus" scoped>
	.content
	 height:66rem
</style>