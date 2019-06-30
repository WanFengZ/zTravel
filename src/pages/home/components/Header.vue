<template>
  <div class="header">
    <div class="header-left">
      <span class="iconfont back-icon">&#xe8b5;</span>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe8d6;</span>
      输入城市/景点/游玩主题
    </div>
    <router-link to="/city">
      <div class="header-right">
        {{this.city}}
        <span class="iconfont arrow-icon">&#xe8d2;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>

<style lang="stylus" scoped>
  @import "~@styles/varibles.styl"
  .header
    display flex
    height $header-height
    line-height $header-height
    background-color $bgColor
    color #fff
    .header-left
      width .64rem
      float left
      .back-icon
        font-size .4rem
        margin-left .2rem
    .header-right
      min-width 1.24rem
      padding 0 .1rem
      float right
      text-align center
      color: #fff
      .arrow-icon
        font-size .24rem
        margin-left -0.06rem
    .header-input
      flex 1
      height .62rem
      line-height .62rem
      margin-top .12rem
      padding-left .2rem
      background-color #fff
      border-radius .1rem
      color #ccc
</style>
