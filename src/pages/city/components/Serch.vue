<template>
  <div>
    <div class="search">
      <input
         type="text"
         class="search-input"
         placeholder="输入城市名或拼音"
         v-model="keyword"
      >
    </div>
    <div class="search-content" ref="search" v-show="keyword">
      <ul>
        <li
          v-for="(item,index) of list"
          :key="index"
          class="search-item border-bottom"
          @click="handleCityClick(item.name)"
        >
          {{item.name}}
        </li>
      </ul>
      <li class="search-item border-bottom" v-show="!list.length">没有找到搜索内容</li>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
export default {
  name: 'CitySerch',
  data () {
    return {
      timer: null,
      keyword: '',
      list: []
    }
  },
  props: {
    cities: Object
  },
  methods: {
    handleCityClick (city) {
      this.$router.push('/')
      this.$store.dispatch('changeCity', city)
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.search, {mouseWhell: true, click: true, tap: true})
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach((value) => {
            if (value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        this.list = result
      }, 100)
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~style/varibles.styl'
  .search
    background: $bjcolor
    height: 1.44rem
    padding: 0 .2rem
    .search-input
      text-align: center
      width: 100%
      height: 1.24rem
      line-height: 1.24rem
      color: #666
      box-sizing: border-box
      padding: 0 .2rem
  .search-content
    position: absolute
    top: 3.2rem
    z-index: 1
    background: #fff
    overflow: hidden
    left: 0
    right: 0
    bottom: 0
    .search-item
      line-height: 1rem
      color: #666
      padding-left: .4rem
</style>
