<template>
  <div>
    <router-link to="/" class="header-abs" tag="div" v-show="showHeader">
      <div class="iconfont back-abs-icon">&#xe624;</div>
    </router-link>
    <div class="header-fixed" v-show="!showHeader" :style="opacityStyle">
      景点选择
      <router-link to="/">
        <div class="iconfont back-icon">&#xe624;</div>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showHeader: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {
          opacity
        }
        this.showHeader = false
      } else {
        this.showHeader = true
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl';
  .header-abs
    position: absolute;
    width: .8rem;
    height: .8rem;
    line-height: .8rem;
    top: .2rem
    left: .2rem
    border-radius: .4rem
    background-color: rgba(0, 0, 0, .8);
    text-align: center
    .back-abs-icon
      color: #fff
  .header-fixed
    z-index: 2
    position: fixed
    overflow: hidden;
    width: 100%;
    height: $headerHeight;
    line-height: $headerHeight;
    background-color: $bgColor;
    text-align: center
    color: #FFF
    font-size: .32rem
    top: 0
    .back-icon
      position: absolute;
      font-size: .32rem
      font-weight: bold
      top: 0
      left: .15rem
      color: #FFF
</style>
