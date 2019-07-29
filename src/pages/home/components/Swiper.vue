<template>
	<div class="swiper">
		<swiper :options="swiperOption">
			<swiper-slide v-for="item of swiperList" :key="item.id">
			<img  class="swiper-img" :src="item.imgUrl" alt="">
			</swiper-slide>
			<div class="swiper-pagination"  slot="pagination"></div>
		</swiper>
	</div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      },
      swiperList: [{
        id: '001',
        imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20197/48925f79599e534dcfa63ae4d7d2bcb6.jpg_750x200_021dc50a.jpg'
      }, {
        id: '002',
        imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20197/e43d3043ee612ad71dd6c68f29e3ed9a.jpg_750x200_b90f2963.jpg'
      }]
    }
  }
}
</script>

<style lang="stylus" scoped>
	.swiper >>> .swiper-pagination-bullet
		background-color: #fff
	.swiper
		overflow: hidden;
		width: 100%;
		height: 0;
		padding-bottom: 26.67%;
		background-color: #eee;
		.swiper-img
			width: 100%
</style>
