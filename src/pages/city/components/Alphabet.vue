<template>
	<ul class="list">
		<li class="item" v-for="(alp,key) of cities">{{key}}</li>
	</ul>
</template>

<script>
export default {
	name: "CityAlphabet",
	props: {
		cities: Object
	}
}
</script>

<style lang="stylus" scoped>	
@import '~styles/varibles.styl'
	.list
		display: flex
		flex-direction: column
		justify-content: center
		position: absolute
		top: 1.6rem 
		right: 0
		bottom: 0
		width: .4rem
		// background-color: red
		.item
			font-size: .3rem
			text-align: center
			line-height: .4rem
			color: $bgColor
</style>