<template>
  <div>
    <div class="title">周末去哪儿</div>
    <div v-for="item of WeekendList" :key="item.id">
      <div class="img-box">
        <img :src="item.imgUrl">
      </div>
      <div class="desc desc-1">{{item.desc}}</div>
      <div class="desc desc-2">{{item.title}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  props: {
    WeekendList: Array
  }
}
</script>

<style lang="stylus">
  .title
    margin-top: .4rem
    background: #eee
    height: 1.8rem
    line-height: 1.8rem
    text-indent: .5rem
  .img-box
    background #eeeeee
    width: 100%
    img
      width: 100%
  .desc
    margin-top: .5rem
    margin-left: .5rem
  .desc-2
    font-size: .9rem
    color: #eee
</style>
