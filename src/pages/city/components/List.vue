<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">
              {{ currentCity }}
            </div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper" v-for="hot of hotCities" :key="hot.id" @click="handleCityClick(hot.name)">
            <div class="button">{{ hot.name }}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(city, key) of cities" :key="key">
        <div class="title border-topbottom" :ref="key">{{ key }}</div>
        <div class="item-list">
          <div class="item border-bottom" v-for="innerCity of city" :key="innerCity.id" @click="handleCityClick(innerCity.name)">
            {{ innerCity.name }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'
export default {
  name: 'CityList',
  props: {
    cities: Object,
    hotCities: Array,
    letter: String
  },
  computed: {
    ...mapState({
      currentCity: 'city'
    })
  },
  watch: {
    letter (val) {
      const element = this.$refs[this.letter][0]
      this.scroll.scrollToElement(element)
    }
  },
  methods: {
    ...mapMutations(['changeCity']),
    handleCityClick (city) {
      // this.$store.commit('changeCity', city)
      this.changeCity(city)
      this.$router.push('/')
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper, {
      click: true
    })
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibies.styl'
  .border-topbottom
    &:before
      border-color #ccc
    &:after
      border-color #ccc
  .border-bottom
    &:before
      border-color #ccc
  .list
    position absolute
    overflow hidden
    top 1.58rem
    left 0
    right 0
    bottom 0
    .title
      line-height .54rem
      background #eee
      padding-left .2rem
      color #666
    .button-list
      overflow hidden
      padding .1rem .6rem .1rem .1rem
      .button-wrapper
        float left
        width 33.33%
        .button
          padding .1rem 0
          margin .1rem
          text-align center
          border .02rem solid #ccc
          border-radius .06rem
    .item-list
      .item
        line-height .54rem
        color #666
        padding-left: .2rem
</style>
