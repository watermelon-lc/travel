<template>
  <div>
    <div class="search">
      <input class="search-input" type="text" placeholder="输入城市名或拼音" v-model="keyword">
    </div>
    <div ref="search" class="search-content" v-show="keyword">
      <ul>
        <li class="search-item border-bottom" v-for="city in list" :key="city.id" @click="handleCityClick(city.name)">
          {{ city.name }}
        </li>
        <li class="search-item border-bottom" style="text-align: center;" v-show="hasNoData">
          没有找到匹配数据
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { mapMutations } from 'vuex'
import Bscroll from 'better-scroll'
export default {
  name: 'CitySearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null
    }
  },
  watch: {
    keyword (val) {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        let result = []
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
  },
  computed: {
    hasNoData () {
      return !this.list.length
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
    this.scroll = new Bscroll(this.$refs.search)
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibies.styl'
  .search
    height .72rem
    background $bgColor
    padding 0 .1rem
    .search-input
      box-sizing border-box
      line-height .62rem
      width 100%
      text-align center
      border-radius .06rem
      color #666
      padding 0 .1rem
  .search-content
    overflow hidden
    position absolute
    top 1.58rem
    left 0
    right 0
    bottom 0
    z-index 1
    background #eee
    .search-item
      line-height .62rem
      padding-left .2rem
      color #666
      background #fff
</style>
