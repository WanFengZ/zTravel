<template>
  <div>
    <div class="recommend-title">周末去哪儿</div>
    <ul>
      <li class="item" v-for="item of weekendList" :key="item.id">
        <div class="item-img-wrapper">
          <img class="item-img" :src="item.imgUrl" alt="">
        </div>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    weekendList: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import '~@styles/mixins.styl'

  .recommend-title
    height .8rem
    line-height .8rem
    background-color #eee
    text-indent .3rem
  .item
    margin .2rem 0
    .item-img-wrapper
      overflow hidden
      height 0
      padding-bottom 37.09%
      .item-img
        width 100%
    .item-info
      padding .1rem
      .item-title
        font-size .32rem
        line-height: .54rem
      .item-desc
        width 88%
        line-height .4rem
        color #aaa
        ellipsis()
</style>
