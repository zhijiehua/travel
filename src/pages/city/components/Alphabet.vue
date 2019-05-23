<template>
  <ul class="list">
      <li
        class="item"
        v-for="item of letters"
        :key="item"
        :ref="item"
        @click="handleLetterClick"
        @touchmove="handleTourchMove"
        @touchstart="handleTourchStart"
        @touchend="handleTourchEnd"
      >
        {{item}}
      </li>
  </ul>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  data () {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  methods: {
    handleLetterClick: function (e) {
      this.$emit('change', e.target.innerText)
    },
    handleTourchStart: function () {
      this.touchStatus = true
    },
    handleTourchMove: function (e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const touchY = e.touches[0].clientY - 51
          const index = Math.floor((touchY - this.startY) / 17.2)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    handleTourchEnd: function () {
      this.touchStatus = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~style/varibles.styl'
  .list
    position: absolute
    right: 0
    top: 3.2rem
    width: .8rem
    bottom: 0
    display: flex
    flex-direction: column
    justify-content: center
    color: $bjcolor
    .item
      text-align: center
      height: 1.08rem
</style>
