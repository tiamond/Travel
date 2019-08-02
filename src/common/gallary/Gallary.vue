<template>
  <div class="container">
    <div class="swiper">
      <swiper :options="swiperOption">
        <swiper-slide v-for="(item, index) of imgs" :key="index">
        <img  class="swiper-img" :src="item" alt="">
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommonGallary',
  props: {
    imgs: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observer: true,
        observeParents: true
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  .container >>> .swiper-container
    overflow: inherit
  .container
    display: flex;
    flex-direction: column
    justify-content: center
    z-index: 99
    position: fixed;
    left: 0
    right: 0
    top: 0
    bottom: 0
    background-color: #000;
    .swiper
      width: 100%;
      height: 0;
      padding-bottom: 100%;
      .swiper-img
        width: 100%;
      .swiper-pagination
        color: #fff
        position: relative;
        top: 1rem
</style>
