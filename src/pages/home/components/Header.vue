<template>
	<div class="header">
		<div class="header-left">
			<div class="iconfont back-icon">&#xe624;</div>
		</div>
		<div class="header-input">
			<span class="iconfont">&#xe632;</span>
			输入城市/景点/游玩主题
		</div>
		<router-link to="/city">
			<div class="header-right">
				{{this.city}}
				<span class="iconfont arrow-icon">&#xe75d;</span>
			</div>
		</router-link>
	</div>
</template>

<script>
	import {mapState} from 'vuex'
	export default {
		name: "HomeHeader",
		computed: {
			...mapState(['city'])
		}
	}
</script>

<style lang="stylus" scoped>
	@import '~styles/varibles.styl'
	.header
		display: flex
		height: .86rem
		background-color: $bgColor
		color: #fff
		line-height: .86rem
		
		.header-left
			width: .64rem
			float: left
			.back-icon
				text-align: center
				font-size: .4rem
		.header-right
			width: 1.24rem
			float: right
			text-align: center
			font-size: 15px
			color: #fff
			.arrow-icon
				font-size: .28rem
				margin-left: -0.05rem
		.header-input
			flex: 1
			background-color: #FFF
			border-radius: .1rem 
			margin-top: .12rem
			height: .64rem
			margin-left: .2rem
			color: #ccc
			font-size: 15px
			line-height: .64rem
			padding-left: .2rem
</style>