<template>
  <div class="menu">
    <swiper :options="swiperOption" :not-next-tick="notNextTick" ref="mySwiper">
      <swiper-slide class="menu-container" v-for="(page,index) of pages" :key="index">
        <div class="menu-item" v-for="item of page" :key="item.id">
          <div class="menu-img-box">
            <img class="menu-img" :src="item.imgUrl" alt="">
          </div>
          <p class="menu-item-desc">{{item.desc}}</p>
        </div>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeMenu',
  props: {
    menuList: Array
  },
  data () {
    return {
      notNextTick: true,
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationClickable: true
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.menuList.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~@styles/varibles.styl'
  @import '~@styles/mixins.styl'
  .menu
    margin-top .15rem
    .swiper-pagination
      bottom 8px
  .menu >>> .swiper-container
    overflow hidden
    width 100%
    height 0
    padding-bottom 50%
  .menu >>> .swiper-pagination-bullet-active
    background-color $bgColor!important;
  .menu-container
    overflow hidden
    width 100%
    height 0
    padding-bottom 44%
    .menu-item
      overflow hidden
      float left
      width 25%
      height 0
      padding-bottom 22%
      position relative
      .menu-img-box
        box-sizing border-box
        padding 0 .1rem
        position absolute
        top 0
        right 0
        bottom .44rem
        left 0
      .menu-img
        display block
        height 100%
        margin 0 auto
      .menu-item-desc
        position absolute
        left 0
        right 0
        bottom 0
        height .44rem
        text-align center
        line-height .44rem
        color $darkTextColor
        ellipsis()
</style>
