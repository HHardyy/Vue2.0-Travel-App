<template>
	<div>
		<city-header></city-header>
		<serch :cities="cities"></serch>
		<list :cities="cities" :hot="hotCities" :latter="latter"></list>
		<alphalet @change="alPhaletFuncchange" :cities="cities"></alphalet>
	</div>
</template>
<script>
import CityHeader from './components/header.vue'
import Serch from './components/serch.vue'
import List from './components/list.vue'
import Alphalet from './components/alphalet.vue'
import axios from 'axios'
	export default {
		name : "city",
		components:{
			CityHeader,
			Serch,
			List,
			Alphalet
		},
		data(){
			return {
				hotCities:[],
				cities:{},
				latter:''
			}
		},
		methods:{
			getINfo(){
				axios.get('/api/city.json')
				.then(this.getInfoData)
				.catch(this.daTaerr)
			},
			getInfoData(responsText){
				const res=responsText.data
				if (res.data) {
					const data=res.data
					this.hotCities=data.hotCities
					this.cities=data.cities
				}
			},
			daTaerr(errData){
				console.log(errData)
			},
			alPhaletFuncchange(latter){
				this.latter=latter
			}
		},
		mounted(){
			this.getINfo()
		}
	}
</script>
<style lang="stylus" scoped>
	@import '~@/assets/styles/varyble.styl'
</style>