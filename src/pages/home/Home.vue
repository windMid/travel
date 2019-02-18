<template>
	<div>
		<HomeHeader></HomeHeader>
		<HomeSwiper :swiperList="swiperList"></HomeSwiper>
		<HomeIcons :iconList="iconList"></HomeIcons>
		<HomeRecommend :recommendList="recommendList"></HomeRecommend>
		<HomeWeekend :weekendList="weekendList"></HomeWeekend>
		<router-view/>
	</div>
</template>

<script>
import HomeHeader from './components/Header.vue'
import HomeSwiper from './components/Swiper.vue'
import HomeIcons  from './components/Icons.vue'
import HomeRecommend from './components/Recommend.vue'
import HomeWeekend from './components/Weekend.vue'
import {mapState} from 'vuex'
import axios from 'axios'
export default {
	name: "Home",
	components:{
		HomeHeader,
		HomeSwiper,
		HomeIcons,
		HomeRecommend,
		HomeWeekend
	},
	data() {
		return {
			swiperList: [],
			iconList: [],
			recommendList: [],
			weekendList: [],
			lastCity: ''
		}
	},
	computed: {
		...mapState(['city'])
	},
	methods: {
		getHomeInfo() {
			axios.get('/api/index.json?city=' + this.city).then(this.getHomeInfoSucc)
		},
		getHomeInfoSucc(res) {
			res=res.data
			if(res.ret && res.data){
				const data = res.data
				this.swiperList = data.swiperList
				this.iconList = data.iconList
				this.recommendList = data.recommendList
				this.weekendList = data.weekendList
			}
			console.log(res)
		}
	},
	mounted () {
		this.getHomeInfo()
		this.lastCity = this.city
	},
	activated() {
		if(this.lastCity !== this.city){
			this.lastCity = this.city
			this.getHomeInfo()
		}
	}
}
</script>

<style>
	
</style>