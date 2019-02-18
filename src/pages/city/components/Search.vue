<template>
	<div class="sear">
		<div class="search">
			<input v-model="keyword" class="search-input" type="text" placeholder="输入城市名或拼音">
		</div>
		<div class="search-content" ref="wrapper"  v-show="keyword">
			<ul>
				<li v-for="item of list" class="search-line" @click="handleCityClick(item.name)">{{item.name}}</li>
				<li class="search-line" v-if="hasnodata">没有找到匹配数据</li>
			</ul>
		</div>
	</div>
</template>

<script>
import Bscroll from 'better-scroll'
export default {
	name: "CitySearch",
	props: {
		cities: Object
	},
	data() {
		return {
			keyword: '',
			list: [],
			timer: null
		}
	},
	computed: {
		hasnodata() {
			return !this.list.length;
		}
	},
	watch: {
		keyword() {
			if(this.timer) {
				clearTimeout(this.timer)
			}
			this.timer = setTimeout(() => {
				const result = []
				for (let i in this.cities) {
					this.cities[i].forEach((value) => {
						if(value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1) {
							result.push(value)
						}
					})
				}
				this.list = result
			}, 100)
		}
	},
	mounted() {
		this.scroll = new Bscroll(this.$refs.wrapper, {click: true})
	},
	methods: {
		handleCityClick(city) {
			this.$store.dispatch('changeCity', city)
			this.keyword = ''
			this.$router.push('/')
		}
	}
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
	.search
		background-color: $bgColor
		height: .72rem
		// padding: 0 .1rem

		.search-input
			font-size: .4rem
			width: 96%
			height: .62rem
			line-height: .62rem
			text-align: center
			border-radius: .06rem
			position: absolute 
			left: 2%
			color: #666
	.search-content
		z-index: 1
		overflow: hidden
		position: absolute
		background-color: #fff
		top: 1.58rem
		left: 0
		right: 0
		bottom: 0
		font-size: .4rem
		.search-line
			font-size: .35rem
			padding: .1rem .1rem
			border-bottom: 1px solid #eee
</style>