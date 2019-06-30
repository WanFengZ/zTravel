<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">深圳</div>
          </div>
        </div>
      </div>
      <div class="area border-topbottom">
        <div class="title">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper" v-for="item of hotCities" :key="item.id">
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area border-topbottom" v-for="(item,key) of cities" :key="key" :ref="key">
        <div class="title">{{key}}</div>
        <ul class="item-list">
          <li class="item border-bottom" v-for="innerItem of item" :key="innerItem.id">{{innerItem.name}}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'CityList',
  props: {
    cities: Object,
    hotCities: Array,
    letter: String
  },
  watch: {
    letter () {
      if (this.letter) {
        this.scroll.scrollToElement(this.$refs[this.letter][0])
      }
    }
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper)
  }
}
</script>

<style lang="stylus" scoped>
  .border-topbottom
    &:before
      border-color #ccc
    &:after
      border-color #ccc
  .border-bottom
    &:before
      border-color #ccc
  .list
    position absolute
    top: 1.60rem
    right: 0
    left: 0
    bottom: 0
    overflow hidden
    .title
      line-height .58rem
      background-color: #eee
      padding-left .2rem
      color #666
      font-size .26rem
    .button-list
      overflow hidden
      padding .1rem
      padding-right .6rem
      .button-wrapper
        float left
        width 33.33%
        .button
          margin .1rem
          text-align center
          line-height .5rem
          border .02rem solid #ccc
          border-radius .1rem
    .item-list
      display block
      line-height .76rem
      padding-left .2rem
</style>
