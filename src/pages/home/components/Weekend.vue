<template>
	<div>
		<div class="recommend-title">周末去哪儿</div>
		<ul>
			<li class="item border-bottom" v-for="item of recommendList" :key="item.id">
				<div class="item-img-wrapper">
					<img :src="item.imgUrl" alt="" class="item-img">
				</div>
				<div class="item-info">
					<p class="item-title">{{item.title}}</p>
					<p class="item-desc">{{item.desc}}</p>
				</div>
			</li>
		</ul>
	</div>
</template>

<script>
export default {
	name: "HomeWeekend",
	data () {
		return {
			recommendList: [{
				id: '0001',
				imgUrl: 'http://img1.qunarzz.com/sight/source/1811/52/b6776b49d27025.jpg_r_640x214_35ae205c.jpg',
				title: '美丽普陀山',
				desc: '人间仙境杭州，佛教圣地普陀山等你来玩！'
			}, {
				id: '0002',
				imgUrl: 'http://img1.qunarzz.com/sight/source/1505/a3/9c9d78e925e8bc.jpg_r_640x214_74656d68.jpg',
				title: '泡汤好去处',
				desc: '泡在氤氲的温泉中，聆听冬天脚步的声音'
			}, {
				id: '0003',
				imgUrl: 'http://img1.qunarzz.com/sight/source/1510/c1/afe3ab32b3bc23.jpg_r_640x214_beb61760.jpg',
				title: '精致暖汤',
				desc: '天然高品质温泉，只是冬天秀美容颜首选之地'
			}]
		}
	}
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
		height: 4rem
		// background-color: red
		overflow: hidden
		.item-img-wrapper
			height: 0
			width: 100%
			padding-bottom: 36.69%
			.item-img
				display: inline-block
				width: 100%
		.item-info
			min-width: 0
			height: 1.2rem
			padding: .15rem
			border-bottom: 1rem #000
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

</style>