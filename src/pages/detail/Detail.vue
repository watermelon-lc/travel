<template>
  <div>
    <DetailBanner :bannerInfo="bannerInfo"></DetailBanner>
    <DetailHeader></DetailHeader>
    <DetailList :list="categoryList"></DetailList>
    <div style="height: 50rem;"></div>
  </div>
</template>

<script>
import DetailBanner from './components/Banner.vue'
import DetailHeader from './components/Header.vue'
import DetailList from './components/List.vue'
import axios from 'axios'
export default {
  name: 'Detail',
  components: { DetailBanner, DetailHeader, DetailList },
  data () {
    return {
      categoryList: [],
      bannerInfo: {}
    }
  },
  methods: {
    getDetailInfo () {
      axios.get('/api/detail.json', {
        params: {
          id: this.$route.params.id
        }
      })
        .then(this.getDetailInfoSucc)
    },
    getDetailInfoSucc (res) {
      let data = res.data.data
      this.bannerImg = data.bannerImg
      this.gallaryImgs = data.gallaryImgs
      this.bannerInfo = {
        sightName: data.sightName,
        bannerImg: data.bannerImg,
        gallaryImgs: data.gallaryImgs || []
      }
      this.categoryList = data.categoryList
    }
  },
  mounted () {
    this.getDetailInfo()
  }
}
</script>

<style lang="stylus" scoped>

</style>
