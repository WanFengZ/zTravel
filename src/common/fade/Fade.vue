<template>
  <transition>
    <slot name="header"></slot>
  </transition>
</template>

<script>
export default {
  name: 'CommonFade'
}
</script>

<style lang="stylus" scoped>
  .v-enter, .v-leave-to
    opacity 0
  .v-enter-active, .v-leave-active
    transition opacity .8s
</style>
