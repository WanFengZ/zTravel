<template>
  <div>
    <home-header></home-header>
    <home-swiper></home-swiper>
    <home-menu></home-menu>
    <home-recommend></home-recommend>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeMenu from './components/Menu'
import HomeRecommend from './components/Recommend'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeMenu,
    HomeRecommend
  }
}
</script>

<style>

</style>
