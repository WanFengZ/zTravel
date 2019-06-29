<template>
  <div>
    <home-header></home-header>
    <home-swiper></home-swiper>
    <home-menu></home-menu>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeMenu from './components/Menu'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeMenu
  }
}
</script>

<style>

</style>
