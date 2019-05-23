<template>
  <div class='wrapper'>
    <swiper :options="swiperOption">
      <swiper-slide v-for='item of SwiperList' :key="item.id">
        <img class="swiper-img" :src='item.imgUrl' />
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  props: {
    SwiperList: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      }
    }
  }
}
</script>

<style lang='stylus' scopde>
  .wrapper
    overflow: hidden
    width: 100%
    height: 0
    padding-bottom: 30%
    background: #eee
    .swiper-img
      width: 100%
</style>

<style>
  .swiper-pagination-bullet-active{
    background: #fff;
  }
</style>
