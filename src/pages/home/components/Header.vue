<template>
    <div class='header'>
      <div class='header-left'>
        <span class="iconfont">&#xe624;</span>
      </div>
      <div class='header-input'>
        <span class="iconfont">&#xe632;</span>
        输入城市/游玩景点/主题
      </div>
      <router-link to="./city">
        <div class='header-right'>
          {{this.$store.state.city}}
          <span class="iconfont">&#xe64a;</span>
        </div>
      </router-link>
    </div>
</template>

<script>
export default {
  name: 'HomeHeader'
}
</script>

<style lang="stylus" scoped>
  @import '~style/varibles.styl'
  .header
    display: flex
    line-height: 1.72rem
    background: $bjcolor
    color: #fff
    .header-left
      text-align: center
      width: 1.28rem
      float: left
    .header-input
      flex: 1
      margin-left: .4rem
      margin-top: .24rem
      height: 1.28rem
      line-height: 1.28rem
      background: #fff
      border-radius: .2rem
      color: #ccc
    .header-right
      color: #fff
      width: 5rem
      text-align: center
      float: right
</style>
