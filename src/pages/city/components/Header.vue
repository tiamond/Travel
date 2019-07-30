<template>
  <div class="header">
    城市选择
    <router-link to="/">
      <div class="iconfont back-icon">&#xe624;</div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl';
  .header
    position: relative
    overflow: hidden;
    height: $headerHeight;
    line-height: $headerHeight;
    background-color: $bgColor;
    text-align: center
    color: #FFF
    font-size: .32rem
    .back-icon
      position: absolute;
      font-size: .32rem
      font-weight: bold
      top: 0
      left: .15rem
      color: #FFF
</style>
