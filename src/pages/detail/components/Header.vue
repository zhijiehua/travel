<template>
  <div>
      <router-link
        class="header-abs"
        tag="div"
        to="/"
        v-show="showAbs"
      >
          <span class="iconfont header-abs-back">&#xe624;</span>
      </router-link>
      <div
        class="header-fixed"
        v-show="!showAbs"
        :style="opacityStyle"
      >
        景点详情
      </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        this.showAbs = false
      } else {
        this.showAbs = true
      }
      if (top > 60 && top < 140) {
        let opacity = top / 140
        this.opacityStyle = {
          opacity
        }
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import '~style/varibles.styl'
  .header-abs
    position: absolute
    top: .4rem
    left: .4rem
    width: 1.2rem
    height: 1.2rem
    text-align: center
    line-height: .8rem
    border-radius: .6rem
    background: rgba(0, 0, 0, .8)
    .header-abs-back
      color: #fff
      font-size: .4rem
  .header-fixed
    z-index: 2
    background: $bjcolor
    position: fixed
    top: 0
    right: 0
    left: 0
    height: $HeaderHeight
    line-height: $HeaderHeight
    text-align: center
    color: #fff
    font-size: .64rem
</style>
