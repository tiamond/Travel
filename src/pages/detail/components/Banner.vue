<template>
  <div>
    <div class="banner" @click="handleClickBanner">
      <img class="banner-img" :src="bannerImg">
      <div class="banner-info">
        <div class="banner-tittle">{{sightName}}</div>
        <div class="banner-number">
          <span class="iconfont">&#xe606;</span>
          {{gallaryImgs.length}}
        </div>
      </div>
    </div>
    <common-gallary :imgs="gallaryImgs" v-show="showGallary" @click.native="handleClickGallary"></common-gallary>
  </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
export default {
  name: 'DetailBanner',
  props: {
    bannerImg: String,
    sightName: String,
    gallaryImgs: Array
  },
  components: {
    CommonGallary
  },
  data () {
    return {
      showGallary: false
    }
  },
  methods: {
    handleClickBanner () {
      this.showGallary = true
    },
    handleClickGallary () {
      this.showGallary = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    position: relative
    overflow: hidden
    height: 0
    padding-bottom: 55%
    .banner-img
      width: 100%
    .banner-info
      position: absolute
      display: flex
      line-height: .6rem
      left: 0
      right: 0
      bottom: 0
      color: #fff
      background-image: linear-gradient(top, rgba(0, 0, 0, 0.0), rgba(0, 0, 0, .8))
      .banner-tittle
        flex: 1
        font-size: .28rem
        padding: 0 .2rem
      .banner-number
        height: .32rem
        line-height: .32rem
        margin-top: .14rem
        padding: 0 .4rem;
        border-radius: .2rem
        background-color: rgba(0, 0, 0, .8)
        font-size: .24rem
        .iconfont
          font-size: .24rem
</style>
