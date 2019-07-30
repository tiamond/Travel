<template>
<div class="header">
  <div class="header-left">
    <div class="iconfont back-icon">&#xe624;</div>
  </div>
  <div class="header-input">
    <span class="iconfont">&#xe632;</span>
    <input class="input" placeholder="输入城市/景点/游玩主题">
  </div>
  <router-link to="/city">
    <div class="header-right">
      {{city}}<span class="iconfont arrow-icon">&#xe64a;</span>
    </div>
  </router-link>
</div>
</template>

<script>
export default {
  name: 'HomeHeader',
  props: {
    city: String
  }
}
</script>

<style lang="stylus" scoped>
/* 1rem = html font-size = 50px */
/* @import '../../../assets/styles/varibles.styl'; */
/* eslint-disable */
  @import '~styles/varibles.styl';
  .header
    display: flex
    line-height: $headerHeight
    background: $bgColor
    color: #fff
    .header-left
      width: .64rem
      float: left
      .back-icon
        text-align: center
        font-weight: bold
        font-size: .32rem
    .header-input
      flex: 1
      height: .62rem
      line-height: .62rem
      margin-top: .12rem
      background: #fff
      border-radius: .1rem
      padding-left: .2rem
      color: #ccc
      .input
        position: relative;
        top: -.05rem
    .header-right
      width: 1.24rem
      float: right
      text-align: center
      color: #FFF
      .arrow-icon
        font-size: .24rem
</style>
