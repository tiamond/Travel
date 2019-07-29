<template>
  <div>
    <div class="title">热销推荐</div>
    <ul>
      <li class="item border-bottom"
          v-for="item of list"
          :key="item.id"
      >
        <img class="item-img" :src="item.imgUrl">
        <div class="item-info">
          <p class="info-title">{{item.title}}</p>
          <p class="info-desc">{{item.desc}}</p>
          <button class="info-btn">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl';
  @import '~styles/mixins.styl'
  .title
    margin-top: .1rem;
    height: .8rem;
    line-height: .8rem;
    text-indent: .2rem
    background-color: #eee;
  .item
    overflow: hidden;
    display: flex;
    height: 2rem;
    .item-img
      width: 1.8rem;
      height: 1.8rem;
      padding: .1rem;
    .item-info
      flex: 1
      padding: .1rem;
      min-width: 0
      .info-title
        line-height: .54rem;
        font-size: .32rem
        ellipsis()
      .info-desc
        line-height: .4rem;
        color: #bbb
        ellipsis()
      .info-btn
        background: #ff9300;
        line-height: .44rem;
        margin-top: .2rem;
        padding:0 .2rem;
        border-radius: .06rem
        color: #FFF
</style>
