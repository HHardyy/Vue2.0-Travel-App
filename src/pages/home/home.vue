<template>
	<div>
		<home-header></home-header>
		<home-swiper :list="list"></home-swiper>
		<icons :iconlist="iconlist"></icons>
		<Recommend :recommend="recommend"></Recommend>
		<Weekcommend :weekcommend="weekcommend"></Weekcommend>
	</div>
</template>

<script>
import HomeHeader from './components/header'
import HomeSwiper from './components/swiper.vue'
import Icons from './components/icons.vue'
import Recommend from './components/recommend.vue'
import Weekcommend from './components/weekcommend.vue'
import axios from 'axios'
	export default {
		name : 'home',
		components:{
			HomeHeader,
			HomeSwiper,
			Icons,
			Recommend,
			Weekcommend
		},
		data(){
			return {
				city:'',
				list:[],
				iconlist:[],
				recommend:[],
				weekcommend:[]
			}
		},
		methods:{
			getHomeData(){
				axios.get('/api/index.json?city=' + this.city)
				.then(this.getsucc)
				.catch(this.geterror)
			},
			getsucc(res){
				res=res.data
				if (res.data&&res.ret) {
					const data=res.data
					this.city=data.city
					this.list=data.swiperList
					this.iconlist=data.iconList
					this.recommend=data.recommendList
					this.weekcommend=data.weekendList
				}
			},
			geterror(error){
				console.log(error)
			}
		},
		mounted(){
			this.getHomeData()
		}
	}
</script>

<style>

</style>