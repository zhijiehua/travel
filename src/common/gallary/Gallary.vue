<template>
  <div class="container" @click="containerClick">
      <div class="wrapper">
        <swiper :options='swiperOptions'>
          <swiper-slide v-for="(item, index) of imgs" :key="index">
            <img class="gallary-img" :src='item' />
          </swiper-slide>
          <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommonGallary',
  data () {
    return {
      swiperOptions: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observeParents: true,
        observer: true
      }
    }
  },
  props: {
    imgs: {
      type: Array,
      default () {
        return []
      }
    }
  },
  methods: {
    containerClick: function () {
      this.$emit('close')
    }
  }
}
</script>

<style lang="stylus" scoped>
  .container >>> .swiper-container
    overflow: inherit
  .container
    left: 0
    top: 0
    right: 0
    bottom: 0
    background: #000
    z-index: 99
    position: fixed
    display: flex
    flex-direction: column
    justify-content: center
    .wrapper
      height: 0
      width: 100%
      padding-bottom: 100%
      background:#000
      .gallary-img
        width: 100%
        height: 100%
      .swiper-pagination
        color: #fff
        bottom: -3rem
</style>
