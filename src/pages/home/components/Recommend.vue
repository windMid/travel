<template>
	<div>
		<div class="recommend-title">热销推荐</div>
		<ul>
			<li class="item border-bottom" v-for="item of recommendList" :key="item.id">
				<div class="item-img-wrapper">
					<img :src="item.imgUrl" alt="" class="item-img">
				</div>
				<div class="item-info">
					<p class="item-title">{{item.title}}</p>
					<p class="item-desc">{{item.desc}}</p>
					<button class="item-button">查看详情</button>
				</div>
			</li>
		</ul>
	</div>
</template>

<script>
export default {
	name: "HomeRecommend",
	props: {
		recommendList: Array
	}
	// data () {
	// 	return {
	// 		recommendList: [{
	// 			id: '0001',
	// 			imgUrl: 'http://img1.qunarzz.com/sight/p0/1810/cc/cc47164357acbeb5a3.water.jpg_200x200_151f0405.jpg',
	// 			title: '大连圣亚海洋世界',
	// 			desc: '浪漫大连首站，浪漫的海洋主题乐园'
	// 		}, {
	// 			id: '0002',
	// 			imgUrl: 'http://img1.qunarzz.com/sight/p0/1810/cc/cc47164357acbeb5a3.water.jpg_200x200_151f0405.jpg',
	// 			title: '大连圣亚海洋世界',
	// 			desc: '浪漫大连首站，浪漫的海洋主题乐园'
	// 		}, {
	// 			id: '0003',
	// 			imgUrl: 'http://img1.qunarzz.com/sight/p0/1810/cc/cc47164357acbeb5a3.water.jpg_200x200_151f0405.jpg',
	// 			title: '大连圣亚海洋世界',
	// 			desc: '浪漫大连首站，浪漫的海洋主题乐园'
	// 		}]
	// 	}
	// }
}
</script>

<style lang="stylus" scoped>
@import '~styles/mixins.styl'
	.recommend-title
		font-size: 20px
		line-height: .8rem
		background-color: #eee
		text-indent: .2rem
	.item
		display: flex
		height: 1.9rem
		// background-color: red
		overflow: hidden
		.item-img-wrapper
			.item-img
				height: 1.7rem
				width: 1.7rem
				padding: .1rem
		.item-info
			flex: 1
			min-width: 0
			padding: .1rem
			.item-title
				line-height: .54rem
				font-size: .32rem
				ellipsis()
			.item-desc
				line-height: .4rem
				font-size: .28rem
				color: #ccc
				margin-bottom: -0.35rem
				ellipsis()
			.item-button
				background-color: #ff9300
				padding: 0 .1rem
				border-radius: .06rem
				color: #fff
</style>