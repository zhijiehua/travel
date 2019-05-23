<template>
  <div class="header">
    城市选择
    <router-link to="/">
      <span class="iconfont header-back">&#xe624;</span>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang='stylus' scoped>
  @import '~style/varibles.styl'
  .header
    overflow: hidden
    background: $bjcolor
    color: #fff
    text-align: center
    height: $HeaderHeight
    line-height: $HeaderHeight
    font-size: .64rem
    .header-back
      text-align: center
      width: 1.28rem
      float: left
      color: #fff
</style>
