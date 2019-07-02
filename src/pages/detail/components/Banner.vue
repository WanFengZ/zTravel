<template>
  <div>
    <div class="banner" @click="handleEnter">
      <img class="banner-img" :src="this.bannerImg" alt="">
      <div class="banner-title">{{this.sightName}}</div>
      <div class="banner-number">
        <span class="iconfont">&#xe889;</span>
        39
      </div>
    </div>
    <common-gallery :imgs="this.galleryImgs" v-show="showGallery" @cancel="handleCancel"></common-gallery>
  </div>
</template>

<script>
import CommonGallery from '@common/gallery/Gallery'
export default {
  name: 'DetailBanner',
  components: {
    CommonGallery
  },
  props: {
    sightName: String,
    bannerImg: String,
    galleryImgs: Array
  },
  data () {
    return {
      showGallery: false,
      imgs: [
        'http://img1.qunarzz.com/sight/p0/1604/e0/e074ca39741daad890.water.jpg_r_800x800_0b01554c.jpg',
        'http://img1.qunarzz.com/sight/p0/1604/80/80941a74399235d790.water.jpg_r_800x800_24576495.jpg'
      ]
    }
  },
  methods: {
    handleEnter () {
      this.showGallery = true
    },
    handleCancel () {
      this.showGallery = false
    }
  },
  activated () {
    this.showGallery = false
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    position relative
    overflow hidden
    width 100%
    height 0
    padding-bottom 55%
    .banner-img
      width 100%
    .banner-title
      position absolute
      bottom 0
      left 0
      right 0
      padding-left .2rem
      line-height .86rem
      font-size .36rem
      color: #fff
      background: linear-gradient(rgba(255,255,255,.1),rgba(0,0,0,.8))
    .banner-number
      position absolute
      left .2rem
      bottom .8rem
      padding  .05rem .2rem
      background-color rgba(0,0,0,.6)
      border-radius .2rem
      line-height .4rem
      color #fff
</style>
