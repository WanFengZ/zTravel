<template>
  <div class="wrapper">
    <swiper :options="swiperOption" :not-next-tick="notNextTick" ref="mySwiper">
      <!-- slides -->
      <swiper-slide v-for="item of swiperList" :key="item.id  ">
        <img class="swiper-img" :src="item.imgUrl" alt="">
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  data () {
    return {
      notNextTick: true,
      swiperOption: {
        autoplay: 3000,
        pagination: '.swiper-pagination',
        loop: true
      },
      swiperList: [
        {
          id: '0001',
          imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20196/5e02c14d35097f40d656f455837b63eb.jpg_750x200_adebb937.jpg'
        },
        {
          id: '0002',
          imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20196/9f581f130d65e97c01301661e1e4116f.jpg_750x200_e5b996c3.jpg'
        }
      ]
    }
  }
}
</script>

<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet-active
    background-color #fff!important;
  .wrapper
    overflow hidden
    width 100%
    height 0
    padding-bottom 26.67%
    background-color #ccc
    .swiper-img
      width 100%
    .swiper-pagination {
      bottom 4px
    }
</style>
