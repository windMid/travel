<template>
	<div class="wrapper">
		<swiper :options="swiperOption">
	    <!-- slides -->
	    <swiper-slide v-for="item in swiperList" :key="item.id">
	    	<img class="swiper-img" :src="item.imgUrl" alt="">
	    </swiper-slide>
	    <!-- Optional controls -->
	    <div class="swiper-pagination"  slot="pagination"></div>

	  </swiper>
  </div>
</template>

<script>
export default {
	name: "HomeSwiper",
	data: function() {
		return {
			swiperOption: {
				pagination: '.swiper-pagination',
				loop: true  //循环展示
			},
			swiperList: [{
				id: '0001',
				imgUrl: 'https://imgs.qunarzz.com/ftejia/1810/b6/8c85590caf3462.jpg'
			},{
				id: '0002',
				imgUrl: 'https://img1.qunarzz.com/vc/55/62/56/4e08707f3fb27930df0372f07f.jpg'
			}]
		}
	}
}
</script>

<style lang="stylus" scoped>
	.wrapper >>> .swiper-pagination-bullet-active
		background: #fff !important
	.wrapper
		width: 100%
		height: 0
		overflow: hidden
		padding-bottom: 55%
		background-color: #eee
		.swiper-img
			width: 100%
			height: 204px
</style>