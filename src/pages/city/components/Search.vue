<template>
  <div>
    <div class="search">
      <input class="search-input" v-model="keyword" type="text" placeholder="输入城市名/拼音">
    </div>
    <div v-show="keyword" class="search-content" ref="search">
      <ul>
        <li class="search-item border-bottom" v-for="(item,index) of list" :key="index" @click="handleCityClick(item.name)">{{item.name}}</li>
        <li class="search-item border-bottom" v-show="hasList">没有找到匹配数据</li>
      </ul>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapMutations } from 'vuex'
export default {
  name: 'CitySearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null
    }
  },
  computed: {
    hasList () {
      return !this.list.length
    }
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          console.log(i)
          this.cities[i].forEach((value) => {
            if (value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        this.list = result
      }, 100)
    }
  },
  methods: {
    ...mapMutations(['changeCity']),
    handleCityClick (city) {
      this.changeCity(city)
      this.$router.push('/')
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.search)
  }
}
</script>

<style lang="stylus" scoped>
  @import "~@styles/varibles.styl"
  .search
    height .72rem
    padding 0 .15rem
    background-color $bgColor
    .search-input
      box-sizing border-box
      width 100%
      height .62rem
      padding 0 .2rem
      text-align center
      border-radius .06rem
      color #666
  .search-content
    overflow hidden
    position absolute
    top 1.60rem
    left 0
    right 0
    bottom 0
    z-index 2
    background-color #eee
    .search-item
      line-height .62rem
      padding-left .2rem
      color #666
      background-color #fff
</style>
