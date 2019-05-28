<template>
<div>
  <div class="banner" @click="bannerClick">
    <img
      :src="bannerImg"
      class="banner-img"
    >
    <div class="banner-info">
        <div class="banner-title">
          {{this.sightName}}
        </div>
        <div class="banner-number">
          <span class="iconfont">&#xe637;</span>
          {{this.bannerImgs.length}}
        </div>
    </div>
  </div>
  <common-gallary
    :imgs='bannerImgs'
    v-show="showGallery"
    @close="bannerClick"
  >
  </common-gallary>
</div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
export default {
  name: 'DetailBanner',
  components: {
    CommonGallary
  },
  data () {
    return {
      showGallery: false
    }
  },
  methods: {
    bannerClick: function () {
      this.showGallery = !this.showGallery
    }
  },
  props: {
    sightName: String,
    bannerImg: String,
    bannerImgs: Array
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    height: 0
    overflow: hidden
    padding-bottom: 55%
    position: relative
    .banner-img
      width: 100%
    .banner-info
      position: absolute
      display: flex
      color: #fff
      left: 0
      right: 0
      bottom: 0
      line-height: 1.2rem
      background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, .8rem))
      .banner-title
        flex: 1
        font-size: .64rem
        padding: 0 .4rem
      .banner-number
        padding: 0 .8rem
        margin-top: .3rem
        height: .64rem
        line-height: .64rem
        border-radius: .2rem
        background: rgba(0, 0, 0, .8)
        font-size: .48rem
        .iconfont
          font-size: .48rem
</style>
