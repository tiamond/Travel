<template>
  <div>
    <div class="search">
      <input v-model="keyword" class="search-input" type="text" placeholder="输入城市名或拼音">
    </div>
    <div class="search-content" ref="search" v-show="keyword">
      <ul>
        <li
          class="search-item border-bottom"
          v-for="item of list"
          :key="item.id"
        >
          {{ item.name }}
        </li>
        <li
          class="search-item border-bottom"
          v-show="hasNoData"
        >
          没有找到匹配数据
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
export default {
  name: 'CitySearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null,
      hasNoData: true
    }
  },
  watch: {
    keyword () {
      if (!this.keyword) {
        this.list = []
        return
      }
      if (this.timer) {
        clearTimeout(this.timer)
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach((value) => {
            if (value.name.indexOf(this.keyword) > -1 || value.spell.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        this.list = result
        this.hasNoData = !this.list.length
      }, 100)
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.search)
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl';
  .search
    overflow: hidden;
    height: .72rem;
    background-color: $bgColor;
    padding: 0 .1rem;
    .search-input
      box-sizing: border-box
      width: 100%;
      height: .62rem;
      line-height: .62rem;
      /* text-align: center */
      text-indent: 2.5rem
      border-radius: .06rem
      color: #666
      padding: 0 .1rem;
  .search-content
    z-index: 1
    overflow: hidden;
    position: absolute;
    top: 1.58rem
    left: 0
    right: 0
    bottom: 0
    background-color: #eee;
    .search-item
      background-color: #fff;
      color: #666
      line-height: .62rem;
      padding-left: .1rem;
</style>
