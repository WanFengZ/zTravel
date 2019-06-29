<template>
  <div>
    <div class="recommend-title">热销推荐</div>
    <ul>
      <li class="item border-bottom" v-for="item of recommendList" :key="item.id">
        <img class="item-img"  :src="item.imgUrl" alt="">
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
          <button class="item-button">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  data () {
    return {
      recommendList: [
        {
          id: '0001',
          imgUrl: 'http://img1.qunarzz.com/sight/p0/1906/93/93db3b8f65fb15b4a3.water.jpg_200x200_dd0bb3b9.jpg',
          title: '深圳欢乐谷',
          desc: '玛雅水乐园，夏日玩水好去处'
        },
        {
          id: '0002',
          imgUrl: 'http://img1.qunarzz.com/sight/p0/1905/e6/e683c8cf5e97ce03a3.img.jpg_200x200_4769276c.jpg',
          title: '世界之窗',
          desc: '国际啤酒节清凉一夏，夜场49.9元'
        },
        {
          id: '0003',
          imgUrl: 'http://img1.qunarzz.com/sight/p0/1508/2e/d9363ce50a88c8c5ff5a138c67687cd4.water.jpg_200x200_1c15c8f5.jpg',
          title: '深圳野生动物园',
          desc: '6.29-6.30周末有特惠99.9元/人'
        },
        {
          id: '0004',
          imgUrl: 'http://img1.qunarzz.com/sight/p0/1808/48/48ae3e0f9a3f195ca3.img.jpg_200x200_f2195465.jpg',
          title: 'Skyland未来科技馆',
          desc: '深圳新的亲子游乐打卡圣地'
        }
      ]
    }
  }
}
</script>

<style lang="stylus" scoped>
  .recommend-title
    height .8rem
    line-height .8rem
    background-color #eee
    text-indent .3rem
  .item
    height 1.9rem
    display flex
    margin .2rem 0
  .item-img
    width 1.7rem
    height 1.7rem
    padding .1rem
  .item-info
    flex 1
    padding .1rem
    .item-title
      font-size .32rem
      line-height: .54rem
    .item-desc
      line-height .4rem
      color #aaa
    .item-button
      line-height .44rem
      background-color #ff9300
      padding 0 .2rem
      border-radius  .06rem
      margin-top .16rem

</style>
