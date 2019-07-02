<template>
  <div>
    <detail-banner :sightName="sightName" :bannerImg="this.bannerImg" :galleryImgs="this.galleryImgs"></detail-banner>
    <detail-header></detail-header>
    <detail-list :categoryList="categoryList"></detail-list>
    <div class="content"></div>
  </div>
</template>

<script>
import axios from 'axios'
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  },
  data () {
    return {
      lastDetailPage: '',
      sightName: '',
      bannerImg: '',
      galleryImgs: [],
      categoryList: []
    }
  },
  computed: {
    currentDetailPage () {
      return this.$route.params.id
    }
  },
  methods: {
    getDetailData () {
      axios.get('/api/detail.json', {
        params: {
          id: this.$route.params.id
        }
      }).then(this.getDetailDataSucc)
    },
    getDetailDataSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.sightName = data.sightName
        this.bannerImg = data.bannerImg
        this.galleryImgs = data.galleryImgs
        this.categoryList = data.categoryList
      }
    }
  },
  mounted () {
    this.lastDetailPage = this.currentDetailPage
    this.getDetailData()
  },
  activated () {
    if (this.lastDetailPage !== this.currentDetailPage) {
      this.getDetailData()
    }
    this.lastDetailPage = this.currentDetailPage
  }
}
</script>

<style lang="stylus" scoped>
  .content
    height 50rem
</style>
