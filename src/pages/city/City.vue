<template>
	<div>
		<CityHeader></CityHeader>
		<CitySearch :cities="cities"></CitySearch>
		<CityList :hotcity="hotcity" :cities="cities" :letter="letter"></CityList>
		<CityAlphabet :cities="cities" @change="handleLetterChange"></CityAlphabet>
		<router-view/>
	</div>

</template>

<script>
import CityHeader from './components/Header.vue'
import CitySearch from './components/Search.vue'
import CityList   from './components/List.vue'
import CityAlphabet from './components/Alphabet.vue'
import axios from 'axios'
export default {
	name: "City",
	components: {
		CityHeader,
		CitySearch,
		CityList,
		CityAlphabet
	},
	mounted() {
		this.getCityInfo()
	},
	methods: {
		getCityInfo() {
			axios.get('/api/city.json').then(this.getCityInfoSucc)
		},
		getCityInfoSucc(res) {
			res = res.data
			if(res.ret && res.data)
				this.hotcity = res.data.hotCities
				this.cities  = res.data.cities
				// console.log(this.hotcity) 
		},
		handleLetterChange(letter) {
			// console.log(letter)
			this.letter = letter
		}
	},
	data() {
		return {
			hotcity: [],
			cities: {},
			letter: ''
		}
	}
}
</script>

<style lang="stylus" scoped>
	
</style>