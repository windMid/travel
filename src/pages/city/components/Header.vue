<template>
	<div class="header">
		城市选择
		<router-link to="/" class="aaa">
			<div class="iconfont back-icon">&#xe624;</div>
		</router-link>
	</div>
</template>

<script>
export default {
	name: "CityHeader"
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
	.header
		position: relative
		height: .86rem
		line-height: .86rem
		overflow: hidden
		color: #fff
		text-align: center
		background-color: $bgColor
		font-size: .32rem
		.aaa
			position: fixed
			top: 0
			left: 0
			.back-icon
				width: .64rem
				font-size: .4rem
				text-align: center
				color: #fff
	</style>