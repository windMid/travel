<template>
	<div class="icons">
		<swiper :options="swiperOption">
			<swiper-slide v-for="it of pages">
				<div class="icon"  v-for="item of it" :key="item.id">
					<div class="icon-img">
						<img class="icon-img-content" :src="item.imgUrl" alt="">
						<p class="title">{{item.desc}}</p>
					</div>
				</div>
			</swiper-slide>
			
		</swiper>
	</div>
</template>

<script>
export default {
	name: "HomeIcons",
	props: {
		iconList: Array
	},
	data() {
		return {
			swiperOption: {
				autoplay: false
			}
		}
	},
	// data() {
	// 	return {
	// 		iconList: [{
	// 			id: '0001',
	// 			imgUrl: 'https://f-flightfe-portalcp.qunarzz.com/f_flightfe_portal_f_flightfe_portal/2018/1542193299396_6857743.png',
	// 			desc: '日游'
	// 		}, {
	// 			id: '0002',
	// 			imgUrl: 'https://imgs.qunarzz.com/vc/34/0e/c6/3a293edbd46f9b89551dce5fb9.png_92.png',
	// 			desc: '门票'
	// 		}, {
	// 			id: '0003',
	// 			imgUrl: 'https://imgs.qunarzz.com/vc/9d/ce/9b/c75d54479549f0622cedee0127.png_92.png',
	// 			desc: '玩乐'
	// 		}, {
	// 			id: '0004',
	// 			imgUrl: 'https://f-flightfe-portalcp.qunarzz.com/f_flightfe_portal_f_flightfe_portal/2018/1542193606963_7865647.png',
	// 			desc: '签证'
	// 		}, {
	// 			id: '0005',
	// 			imgUrl: 'https://imgs.qunarzz.com/vc/93/24/e0/a21a64cc7373793c1216edbdbd.png_92.png',
	// 			desc: 'Wi-Fi'
	// 		}, {
	// 			id: '0006',
	// 			imgUrl: 'https://imgs.qunarzz.com/vc/5a/18/c3/cf829c365c2c17253153bff86c.png_92.png',
	// 			desc: '包车'
	// 		}, {
	// 			id: '0007',
	// 			imgUrl: 'https://imgs.qunarzz.com/vc/44/45/8f/35cbaf8962c786da3c9e3d25c1.png_92.png',
	// 			desc: '接送机'
	// 		}, {
	// 			id: '0008',
	// 			imgUrl: 'https://f-flightfe-portalcp.qunarzz.com/f_flightfe_portal_f_flightfe_portal/2018/1542193826942_8473249.png',
	// 			desc: '更多'
	// 		}, {
	// 			id: '0009',
	// 			imgUrl: 'https://f-flightfe-portalcp.qunarzz.com/f_flightfe_portal_f_flightfe_portal/2018/1542193826942_8473249.png',
	// 			desc: '更多'
	// 		}]
	// 	}
	// },
	computed: {
		pages () {
			const pages = []
			this.iconList.forEach((item, index) => {
				const page = Math.floor(index / 8)
				if(!pages[page]){
					pages[page] = []
				}
				pages[page].push(item)
			})
			return pages
		}
	}
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
@import '~styles/mixins.styl'
	.icons >>> .swiper-container
		height: 0
		width: 100%
		padding-bottom: 28%
		overflow: hidden
		background-color: $bgColor
		margin-top: -0.1rem
	.icon
		float: left
		width: 22%
		height: 0
		padding-bottom: 10%
		background-color: #fff
		position: relative
		margin: .15rem .1rem
		border-radius: .2rem 
		.icon-img
			position: absolute
			top: 0
			left: 10%
			right: 1rem
			bottom: 0
			background-color: white
			border-radius: .2rem
			.icon-img-content
				display: block
				margin: auto 0 
				height: 100%
		.title
			font-size: 16px
			position: absolute
			top: 30%
			left: 140%
			height: 1rem
			width: .9rem
			ellipsis()
			
</style>