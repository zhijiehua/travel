<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="bottom-list">
            <div class="bottom-wrapper">
              <div class="bottom">{{this.$store.state.city}}</div>
            </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="bottom-list">
            <div
              class="bottom-wrapper"
              v-for="item of hotCities"
              :key="item.id"
              @click="handleCityClick(item.name)"
            >
              <div class="bottom">{{item.name}}</div>
            </div>
        </div>
      </div>
      <div class="area"
        v-for="(item,key) of cities"
        :key="key"
        :ref="key"
      >
        <div class="title border-topbottom">{{key}}</div>
        <div class="item-list">
            <div class="item border-bottom"
              v-for="innerItem of item"
              :key="innerItem.id"
              @click="handleCityClick(innerItem.name)"
            >
              {{innerItem.name}}
            </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
export default {
  name: 'CityList',
  methods: {
    handleCityClick (city) {
      this.$store.dispatch('changeCity', city)
      this.$router.push('/')
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
  },
  props: {
    cities: Object,
    hotCities: Array,
    letter: String
  },
  watch: {
    letter () {
      const element = this.$refs[this.letter][0]
      this.scroll.scrollToElement(element)
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~style/varibles.styl'
  .border-topbottom
        &:before
          border-color: #ccc
        &:after
          border-color: #ccc
      .border-bottom
        &:before
          border-color: #ccc
  .list
    position: absolute
    top: 3.2rem
    left: 0
    right: 0
    bottom: 0
    overflow: hidden
    .area
      top: 0
      .title
        line-height: 1.48rem
        background: #eee
        color: #666
        font-size: .52rem
        padding-left: .4rem
      .bottom-list
        padding: .2rem 1.2rem .2rem .2rem
        overflow: hidden
        .bottom-wrapper
          float: left
          width: 33.33%
          .bottom
            backgroundcolor: red
            margin: .2rem
            padding: .2rem 0
            text-align: center
            border: .02rem solid #ccc
      .item-list
        .item
          line-height: 1.5rem
          color: #666
          text-indent: .6rem
</style>
