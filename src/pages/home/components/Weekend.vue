<template>
  <div class="weekend">
    <div class="title">周末去哪儿</div>
    <ul>
      <li class="item border-bottom"
          v-for="item of list"
          :key="item.id"
      >
        <div class="item-img-wrap">
          <img class="item-img" :src="item.imgUrl">
        </div>
        <div class="item-info">
          <p class="info-title">{{item.title}}</p>
          <p class="info-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl';
  @import '~styles/mixins.styl';
  .weekend
    background-color: #eee;
    .title
      height: .8rem;
      line-height: .8rem;
      text-indent: .2rem
      background-color: #eee;
    .item
      overflow: hidden;
      height: 0;
      padding-bottom: 49%;
      .item-img-wrap
        overflow: hidden;
        height: 0;
        padding-bottom: 37.5%;
        .item-img
          width: 100%
      .item-info
        overflow: hidden;
        height: 0;
        background-color: #fff;
        padding-bottom: 10.5%;
        .info-title
          color: .32rem
          margin: .1rem;
        .info-desc
          ellipsis()
          text-indent: .1rem
          font-size: .24rem
          margin-top: .1rem;
          color: #616161
</style>
