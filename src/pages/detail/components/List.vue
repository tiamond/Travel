<template>
  <div>
    <div v-for="(item, index) of list" :key="index" class="item">
      <div class="item-title border-bottom">
        <span class="ticket-icon"></span>
        {{ item.title }}
      </div>
      <div v-if="item.children" class="item-children">
        <detail-list :list="item.children"></detail-list>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailList',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  .item-title
    padding-left: .6rem;
    height: .6rem;
    line-height: .6rem;
  .item-children
    padding: 0 .2rem;
  .ticket-icon
    display: inline-block;
    position: absolute;
    width: .36rem;
    height: .36rem;
    top: .2rem;
    left: .2rem;
    background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat;
    margin-right: .1rem;
    background-size: .4rem 3rem;
</style>
