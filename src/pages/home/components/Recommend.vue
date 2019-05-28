<template>
<div>
  <div class="title">热销推荐</div>
  <ul>
    <router-link
      class="item border-bottom"
      v-for="i of RecommendList"
      :key="i.id"
      tag="li"
      :to="'/detail/'+i.id"
    >
      <div class="img-box">
        <img :src="i.imgUrl" class="item-img">
      </div>
      <div class="info">
        <p class="all item-title">{{i.title}}</p>
        <p class="all item-desc">{{i.desc}}</p>
        <button class="class-button">查看详情</button>
      </div>
    </router-link>
  </ul>
</div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    RecommendList: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import '~style/mixins.styl'
  .title
    margin-top: .4rem
    background: #eee
    height: 1.8rem
    line-height: 1.8rem
    text-indent: .5rem
  .item
    display: flex
    .img-box
      float: left
      margin-top: .5rem
      margin-left: .5rem
      width: 6rem
      height: 6rem
      img
        height: 100%
        width: 100%
    .info
      flex: 1
      overflow: hidden
      ellipsis()
      float: right
      margin-left: .3rem
      margin-top: .5rem
      .all
        height: 2rem
        line-height: 2rem
        ellipsis()
      .item-desc
        color: #eee
      .item-button
        height: 1rem
</style>
