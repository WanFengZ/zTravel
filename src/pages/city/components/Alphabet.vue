<template>
  <ul class="list">
    <li class="item" v-for="item of letters"
                     :key="item"
                     :ref="item"
                     @click="handleLetterClick"
                     @touchstart.prevent="handleTouchStart"
                     @touchmove.prevent="handleTouchMove"
                     @touchend.prevent="handleTouchEnd">
      {{item}}
    </li>
  </ul>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  data () {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    }
  },
  computed: {
    letters () {
      return Object.keys(this.cities)
    }
  },
  updated () {
    this.startY = this.$refs[this.letters[0]][0].offsetTop
  },
  methods: {
    handleLetterClick (e) {
      this.$emit('letterClick', e.target.innerText)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const touchY = e.touches[0].clientY - 79
          const index = Math.floor((touchY - this.startY) / 20)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('letterClick', this.letters[index])
          }
        }, 16)
      }
    },
    handleTouchEnd () {
      this.touchStatus = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~@styles/varibles.styl"
  .list
    display flex
    flex-direction column
    justify-content center
    align-items center
    position absolute
    right 0
    top 1.60rem
    bottom 0
    width .8rem
    .item
      line-height .4rem
      text-align center
      color: $bgColor
</style>
