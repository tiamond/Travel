<template>
  <div class="weekend">
    <div class="title">周末去哪儿</div>
    <ul>
      <li class="item border-bottom"
          v-for="item of recommendList"
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
  data () {
    return {
      recommendList: [{
        id: '0001',
        imgUrl: 'http://img1.qunarzz.com/sight/source/1811/52/b6776b49d27025.jpg_r_640x214_35ae205c.jpg',
        title: '杭州浪浪浪水公园',
        desc: '杭州，前世今生与你有一场美丽约会杭州，前世今生与你有一场美丽约会'
      }, {
        id: '0002',
        imgUrl: 'http://img1.qunarzz.com/sight/source/1811/52/b6776b49d27025.jpg_r_640x214_35ae205c.jpg',
        title: '杭州浪浪浪水公园',
        desc: '杭州，前世今生与你有一场美丽约会杭州，前世今生与你有一场美丽约会'
      }, {
        id: '0003',
        imgUrl: 'http://img1.qunarzz.com/sight/source/1811/52/b6776b49d27025.jpg_r_640x214_35ae205c.jpg',
        title: '杭州浪浪浪水公园',
        desc: '杭州，前世今生与你有一场美丽约会杭州，前世今生与你有一场美丽约会'
      }]
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl';
  @import '~styles/mixins.styl';
  .weekend
    background-color: #eee;
    .title
      margin-top: .1rem;
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
          font-weight: bold
        .info-desc
          ellipsis()
          text-indent: .1rem
          font-size: .24rem
          margin-top: .1rem;
          color: #616161
</style>
