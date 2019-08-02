<template>
  <div>
    <detail-banner
      :bannerImg="bannerImg"
      :sightName="sightName"
      :gallaryImgs="gallaryImgs"
    ></detail-banner>
    <detail-header :sightName="sightName"></detail-header>
    <div class="content">
      <detail-list :list="categoryList"></detail-list>
    </div>
  </div>
</template>

<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
import axios from 'axios'
export default {
  name: 'Detail',
  data () {
    return {
      sightName: '',
      bannerImg: '',
      gallaryImgs: [],
      categoryList: [],
      list: [{
        title: '成人票',
        children: [{
          title: '成人票三馆联票'
        }, {
          title: '成人票五馆联票',
          children: [{
            title: '三级目录'
          }]
        }]
      }, {
        title: '学生票'
      }, {
        title: '儿童票'
      }, {
        title: '特惠票'
      }]
    }
  },
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  },
  mounted () {
    this.getDetailInfo()
    console.log(this.$route.params.id)
  },
  methods: {
    getDetailInfo () {
      axios.get('/api/detail.json', {
        params: {
          id: this.$route.params.id
        }
      }).then(this.getDetailInfoSucc)
    },
    getDetailInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.sightName = data.sightName
        this.bannerImg = data.bannerImg
        this.gallaryImgs = data.gallaryImgs
        this.categoryList = data.categoryList
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  .content
    height: 50rem;
</style>
