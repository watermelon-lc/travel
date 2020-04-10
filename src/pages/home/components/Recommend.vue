<template>
  <div>
    <div class="recommend-title">热销推荐</div>
    <ul>
      <router-link
        tag="li"
        class="recommend-item border-bottom"
        v-for="recommend in list"
        :key="recommend.id"
        :to="'/detail/' + recommend.id"
      >
        <div class="item-img-wrapper">
          <img :src="recommend.imgUrl" class="item-img">
        </div>
        <div class="item-info">
          <p class="item-title">{{ recommend.title }}</p>
          <p class="item-desc">{{ recommend.desc }}</p>
          <button class="item-button">查看详情</button>
        </div>
      </router-link>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/mixins.styl'
  .recommend-title
    margin-top .2rem
    line-height .4rem
    background-color #eee
    text-indent .2rem
  .recommend-item
    overflow hidden
    display flex
    height 1.9rem
    .item-img-wrapper
      img
        width 1.7rem
        height 1.7rem
        padding .1rem
    .item-info
      flex 1
      padding .1rem
      min-width 0
      .item-title
        line-height .54rem
        font-size .32rem
        ellipsis()
      .item-desc
        line-height .4rem
        color #ccc
        ellipsis()
      .item-button
        line-height .44rem
        margin-top .2rem
        background #ff9300
        padding 0 .2rem
        border-radius .06rem
        color #fff
</style>
