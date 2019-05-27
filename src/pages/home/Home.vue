<template>
  <div class="home">
    <home-header></home-header>
    <home-swiper :SwiperList="SwiperList"></home-swiper>
    <home-icons :IconsList="IconsList"></home-icons>
    <home-recommend :RecommendList="RecommendList"></home-recommend>
    <home-weekend :WeekendList="WeekendList"></home-weekend>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
import {mapState} from 'vuex'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeWeekend
  },
  computed: {
    ...mapState(['city'])
  },
  data () {
    return {
      lastCity: '',
      SwiperList: [],
      IconsList: [],
      RecommendList: [],
      WeekendList: []
    }
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/index.json?city=' + this.city)
        .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      res = res.data
      this.SwiperList = res.data.swiperList
      this.IconsList = res.data.iconsList
      this.RecommendList = res.data.recommendList
      this.WeekendList = res.data.weekendList
    }
  },
  mounted () {
    this.lastCity = this.city
    this.getHomeInfo()
  },
  activated () {
    if (this.lastCity !== this.city) {
      this.lastCity = this.city
      this.getHomeInfo()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
