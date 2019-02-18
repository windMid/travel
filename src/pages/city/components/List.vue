<template>
	<div class="list" ref="wrapper">
		<div>
			<div class="area">
				<div class="title border-topbottom">当前城市</div>
				<div class="button-list">
					<div class="button-wrapper">
						<div class="button">
							{{this.city}}
						</div>
					</div>
				</div>
			</div>
			<div class="area">
				<div class="title border-topbottom">热门城市</div>
				<div class="button-list">
					<div class="button-wrapper" v-for="item of hotcity" :key="item.id" @click="handleCityClick(item.name)">
						<div class="button">
							{{item.name}}
						</div>
					</div>
				</div>
			</div>

			<div class="area" v-for="(city,key) of cities" :key="key" :ref="key">
				<div class="title border-topbottom">{{key}}</div>
				<div class="item-list">
					<div class="item border-bottom" v-for="single of city" :key="single.id" @click="handleCityClick(single.name)">
						{{single.name}}
					</div>
				</div>
			</div>
			
		</div>
	</div>
</template>

<script>
import Bscroll from 'better-scroll'
import {mapState, mapActions} from 'vuex'
export default {
	name: "CityList",
	props: {
		hotcity: Array,
		cities: Object,
		letter: String
	},
	watch: {
		letter() {
			const element = this.$refs[this.letter][0]
			this.scroll.scrollToElement(element)
		}
	},
	methods: {
		handleCityClick(city) {
			this.changeCity(city)
			this.$router.push('/')
		},
		...mapActions(['changeCity'])
	},
	mounted() {
		this.scroll = new Bscroll(this.$refs.wrapper, {click: true})
	},
	computed: {
		...mapState(['city'])
	}
}
</script>

<style lang="stylus" scoped>
	.list
		overflow: hidden
		position: absolute
		top: 1.6rem
		left: 0
		right: 0
		bottom: 0
		.area
			.title
				line-height: .4rem
				background-color: #eee
				padding-left: .2rem
				color: #666
				font-size: .3rem
			.button-list
				padding: .1rem .6rem .1rem .1rem
				overflow: hidden
				.button-wrapper
					width: 33.33%
					float: left
					.button
						text-align: center
						margin: .1rem
						border: .02rem solid #ccc
						font-size: .4rem
						padding: .1rem 0
						border-radius: .1rem
			.item-list
				.item
					line-height: .76rem
					font-size: .4rem
					padding-left: .2rem
					border-bottom: 1px solid #eaeaea
</style>