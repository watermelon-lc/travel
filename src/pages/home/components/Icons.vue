<template>
  <div class="icons">
    <swiper>
      <swiper-slide v-for="(page, index) in pages" :key="index">
        <div class="icon" v-for="icon in page" :key="icon.id">
          <div class="icon-img">
            <img class="icon-img-content" :src="icon.imgUrl">
            <p class="icon-img-des">{{ icon.desc }}</p>
          </div>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  data () {
    return {
      iconsList: [
        {
          id: '001',
          imgUrl: 'https://picbed.qunarzz.com/01d2f57f920666364197a850dab859a8.png',
          desc: '民宿客栈'
        },
        {
          id: '002',
          imgUrl: 'https://picbed.qunarzz.com/83af731055e121a3251690b225327b56.png',
          desc: '专车自驾'
        },
        {
          id: '003',
          imgUrl: 'https://picbed.qunarzz.com/5b6737be49ca243072ca614f07803b83.png',
          desc: '信用卡'
        },
        {
          id: '004',
          imgUrl: 'https://picbed.qunarzz.com/1e107321f5396ea4994cd832232ecf8a.png',
          desc: '旅游团购'
        },
        {
          id: '005',
          imgUrl: 'https://picbed.qunarzz.com/c65b3bb7571a6bd62df669213e44b84d.png',
          desc: '一日游'
        },
        {
          id: '006',
          imgUrl: 'https://picbed.qunarzz.com/f6bb08a239ce1b038204120a8d1e4669.png',
          desc: '特惠酒店'
        },
        {
          id: '007',
          imgUrl: 'https://picbed.qunarzz.com/3a08f360e958ccb2b947049387873ace.png',
          desc: '借钱'
        },
        {
          id: '008',
          imgUrl: 'https://picbed.qunarzz.com/25e3b9f17a21a6e0113c57a23ffccde4.png',
          desc: '周边短途'
        },
        {
          id: '009',
          imgUrl: 'https://picbed.qunarzz.com/799d9d090d1625a854194460c8849fee.png',
          desc: '邮轮'
        },
        {
          id: '010',
          imgUrl: 'https://picbed.qunarzz.com/19b4f6d2fabd617789fa5aad65b249da.png',
          desc: '白金卡'
        },
        {
          id: '011',
          imgUrl: 'https://picbed.qunarzz.com/f5e5770393d759578962e53ee67798c8.png',
          desc: '海外酒店'
        },
        {
          id: '012',
          imgUrl: 'https://picbed.qunarzz.com/a36d2288f19e54562338f4d8ef986288.png',
          desc: '低价机票'
        }
      ],
      swiperOptions: {
        pagination: {
          el: '.swiper-pagination'
        }
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconsList.forEach((item, index) => {
        const page = Math.floor(index / 10)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibies.styl'
  @import '~styles/mixins.styl'
  .icons >>> .swiper-container
    height 0
    padding-bottom 40%
  .icon
    position relative
    overflow hidden
    float left
    width 20%
    height 0
    padding-bottom 20%
    .icon-img
      position absolute
      top 0
      left 0
      right 0
      bottom .44rem
      box-sizing border-box
      padding .2rem
      .icon-img-content
        display block
        height 100%
        margin 0 auto
      .icon-img-des
        height .44rem
        line-height .44rem
        color $darkTextColor
        text-align center
        font-size .24rem
        ellipsis()
</style>
