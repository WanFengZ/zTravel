<template>
  <div>
    <router-link tag="div" to="/" class="header-abs" v-show="showAbs">
      <span class="header-abs-icon iconfont">&#xe8b5;</span>
    </router-link>
    <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
      景点详情
      <router-link to="/">
        <span class="iconfont header-back">&#xe8b5;</span>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        let opacity = top / 120
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {
          opacity
        }
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import '~@styles/varibles.styl'
  .header-abs
    position absolute
    left .2rem
    top .2rem
    width .8rem
    height .8rem
    border-radius .4rem
    background: rgba(0,0,0,.6)
    color #fff
    .header-abs-icon
      font-size .48rem
      line-height .8rem
      margin-left .26rem
  .header-fixed
    position fixed
    top 0
    left 0
    right 0
    overflow hidden
    height $header-height
    line-height $header-height
    text-align center
    font-size .32rem
    color #fff
    background-color $bgColor
    z-index 2
    .header-back
      width .64rem
      font-size .4rem
      color #fff
      position absolute
      top 0
      left .2rem
</style>
