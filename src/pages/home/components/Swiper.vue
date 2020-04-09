<template>
  <div class="swiper">
    <swiper ref="mySwiper" :options="swiperOptions">
      <swiper-slide v-for="img in swiperList" :key="img.id">
        <img :src="img.imgUrl" class="swiper-img">
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  data () {
    return {
      swiperOptions: {
        pagination: {
          el: '.swiper-pagination'
        },
        loop: true
        // Some Swiper option/callback...
      },
      swiperList: [
        {
          id: '001',
          imgUrl: 'http://imgs.qunarzz.com/vc/e3/a1/71/f498dfd3bed948d623c9093252.jpg_92.jpg'
        },
        {
          id: '002',
          imgUrl: 'http://imgs.qunarzz.com/vc/6d/9f/35/b8ad5468f73fd60ec0ced086f6.jpg_92.jpg'
        },
        {
          id: '003',
          imgUrl: 'http://imgs.qunarzz.com/vc/44/e9/86/95bc36c9e1c06ebd68bdfe222e.jpg_92.jpg'
        }
      ]
    }
  }
}
</script>

<style lang="stylus" scoped>
  .swiper >>> .swiper-pagination-bullet-active
    background #fff
  .swiper
    overflow hidden
    height 0
    padding-bottom 30.60%
    width 100%
    background #eee
    // height 31.25vw
    .swiper-img
      width 100%
</style>
