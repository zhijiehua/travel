<template>
  <div>
      <div
        class="item"
        v-for="(item,index) of list"
        :key="index"
      >
        <div class="item-title border-bottom">
            <span class="item-title-icon"></span>
            {{item.title}}
        </div>
        <div v-show="item.children" class="item-children">
          <detail-list :list="item.children"></detail-list>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'DetailList',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  .item-title
    line-height: 1.6rem
    font-size: .64rem
    padding: 0 .4rem
    .item-title-icon
      display: inline-block
      width: .64rem
      height: .64rem
      background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat;
      margin-right: .2rem
      background-size: .8rem .6rem
  .item-children
    padding: 0 .4rem
</style>
