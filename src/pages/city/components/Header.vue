<template>
  <div class='header'>
    <router-link to = '/'>
      <div class="iconfont back-icon">&#xe624;</div>
    </router-link>
    城市选择
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang='stylus' scoped>
  @import '~styles/variables.styl'
  .header
    height: $headerHeight
    line-height: $headerHeight
    background: $bgColor
    color: #ffffff
    text-align: center
    font-size: .34rem
    .back-icon
      position: absolute
      margin-left: 0
      margin-top: 0
      width: .64rem
      font-size: .4rem
      color: #fff
</style>
