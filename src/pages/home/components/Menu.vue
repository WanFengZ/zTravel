<template>
  <div class="menu">
    <swiper :options="swiperOption" :not-next-tick="notNextTick" ref="mySwiper">
      <swiper-slide class="menu-container" v-for="(page,index) of pages" :key="index">
        <div class="menu-item" v-for="item of page" :key="item.id">
          <div class="menu-img-box">
            <img class="menu-img" :src="item.imageURL" alt="">
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
  data () {
    return {
      notNextTick: true,
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationClickable: true
      },
      menuList: [
        {
          id: '00001',
          imageURL: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
          desc: '景点门票'
        },
        {
          id: '00002',
          imageURL: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20195/b0026eb6f96fd2daecba0d7982c7e4c8.png',
          desc: '六月特惠'
        },
        {
          id: '0003',
          imageURL: 'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png',
          desc: '深圳必游'
        },
        {
          id: '0004',
          imageURL: 'http://img1.qunarzz.com/piao/fusion/1803/50/26ffa31b56646402.png',
          desc: '海洋馆'
        },
        {
          id: '0005',
          imageURL: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20194/bda58ffc3016edad84e656e8a94b0321.png',
          desc: '广州融创'
        },
        {
          id: '0006',
          imageURL: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20194/cba147cf6cfcea7109d0bff6aac6f626.png',
          desc: '深圳动物园'
        },
        {
          id: '0007',
          imageURL: 'http://img1.qunarzz.com/piao/fusion/1803/a6/6d97515091789602.png',
          desc: '世界之窗'
        },
        {
          id: '0008',
          imageURL: 'http://img1.qunarzz.com/piao/fusion/1803/b6/37560ece9c62b502.png',
          desc: '东部华侨城'
        },
        {
          id: '0009',
          imageURL: 'http://img1.qunarzz.com/piao/fusion/1803/3e/86314b2af03b7502.png',
          desc: '水上乐园'
        },
        {
          id: '0010',
          imageURL: 'http://img1.qunarzz.com/piao/fusion/1803/b1/528a9e80403b8c02.png',
          desc: '玩转长隆'
        }
      ]
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
