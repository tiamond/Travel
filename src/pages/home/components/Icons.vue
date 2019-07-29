<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide
        v-for="(page, index) of pages"
        :key="index"
      >
        <div
          class="icon"
          v-for="item of page"
          :key="item.id"
        >
          <div class="icon-img">
            <img class="icon-img-content" :src="item.imgUrl">
            <span class="icon-desc">{{item.desc}}</span>
          </div>
        </div>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: false
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
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
  @import '~styles/varibles.styl';
  @import '~styles/mixins.styl';
  .icons >>> .swiper-container
    overflow: hidden;
    height: 0;
    padding-bottom: 55%;
  .icons >>> .swiper-pagination-bullet-active
    background-color: $bgColor;
  .icons
    margin-top: .1rem;
    .icon
      height: 0;
      overflow: hidden;
      position: relative;
      width: 25%;
      float: left;
      padding-bottom: 25%;
      .icon-img
        position: absolute;
        top: 0
        left: 0
        right: 0
        bottom: .44rem
        padding: .1rem;
        box-sizing: border-box
        .icon-img-content
          display: block;
          margin: 0 auto;
          height: 100%;
      .icon-desc
        display: block;
        margin: 0 auto
        text-align: center
        line-height: .44rem
        font-size: .24rem
        height: .44rem;
        color: $darkTextColor
        ellipsis()
</style>
