<template>
  <div>
    <div class="item" v-for="(item,index) of categoryList" :key="index">
      <div class="item-title border-bottom">
        <span class="item-title-icon"></span>
        {{item.title}}
      </div>
      <div v-if="item.children" class="item-children">
        <detail-list :categoryList="item.children"></detail-list>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailList',
  props: {
    categoryList: Array
  }
}
</script>

<style lang="stylus" scoped>
  .item-title
    position relative
    height .8rem
    line-height .8rem
    font-size .32rem
    padding 0 .6rem
    .item-title-icon
      display: inline-block
      position: absolute
      width: .36rem
      height: .36rem
      top: .26rem
      left: .2rem
      background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat
      margin-right: .1rem
      background-size: .4rem 3rem
  .item-children
    padding 0 .2rem
</style>
