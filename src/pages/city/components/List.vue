<template>
  <div class="list" ref="listWrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.currentCity}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper"
            v-for="item of hot"
            :key="item.id"
            @click="headleCityClick(item.name)"
          >
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div
        class="area"
        v-for="(item, key) of cities"
        :key="key"
      >
        <div class="title border-topbottom" :ref="key">{{key}}</div>
        <div class="item-list">
          <div
            class="item border-bottom"
            v-for="innerItem of item"
            :key="innerItem.id"
            @click="headleCityClick(innerItem.name)"
          >
            {{innerItem.name}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState, mapMutations } from 'vuex'
import BScroll from 'better-scroll'
export default {
  name: 'CityList',
  props: {
    hot: Array,
    cities: Object,
    letter: String
  },
  computed: {
    ...mapState({
      currentCity: 'city'
    })
  },
  methods: {
    headleCityClick (city) {
      // this.$store.commit('changeCity', city)
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  mounted () {
    // this.scrool = new BScroll(this.$refs.listWrapper)
    this.scroll = new BScroll('.list')
  },
  watch: {
    letter () {
      // console.log(this.$refs[this.letter][0])
      this.scroll.scrollToElement(this.$refs[this.letter][0])
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl';
  .border-topbottom
    &::before
      border-color: #ccc
    &::after
      border-color: #ccc
  .border-bottom
      &:before
        border-color: #ccc
  .list
    position: absolute;
    overflow: hidden;
    top: 1.58rem
    bottom: 0
    left: 0
    right: 0
    .title
      padding-left: .2rem;
      height: .60rem;
      line-height: .60rem;
      background-color: #eee;
    .button-list
      box-sizing: border-box
      width: 100%;
      overflow: hidden;
      padding: .1rem .6rem .1rem .1rem;
      .button-wrapper
        width: 33.33%;
        float: left;
        .button
          margin: .1rem;
          padding: .1rem 0;
          text-align: center
          background-color: #ddd;
          border-radius: .06rem
    .item-list
      .item
        line-height: .76rem;
        padding-left: .2rem;
        color: #666
</style>
