<template>
  <div class="header">
    城市选择
    <router-link to="/">
      <span class="iconfont header-back">&#xe8b5;</span>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
  @import '~@styles/varibles.styl'
  .header
    overflow hidden
    height $header-height
    line-height $header-height
    text-align center
    font-size .32rem
    color #fff
    background-color $bgColor
    .header-back
      width .64rem
      font-size .4rem
      color #fff
      position absolute
      top 0
      left .2rem
</style>
