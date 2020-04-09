<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont icon-back">&#xe624;</div>
    </div>
    <div class="header-input">
      <span class="iconfont icon-search">&#xe632;</span>
      输入城市/景点/游玩/主题
    </div>
    <router-link to="/city">
      <div class="header-right">
        {{ city }}
        <span class="iconfont icon-arrow-down">&#xe62f;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'HomeHeader',
  props: {
    city: String
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibies.styl'
  .header
    display flex
    height $headerHeight
    line-height $headerHeight
    background $bgColor
    color #fff
    .header-left
      width .64rem
      float left
      .icon-back
        text-align center
        font-size .4rem
    .header-input
      flex 1
      height .64rem
      line-height .64rem
      margin-top .12rem
      background #fff
      border-radius .1rem
      color #ccc
      text-indent .12rem
    .header-right
      width 1.24rem
      float right
      text-align center
      color #fff
      .icon-arrow-down
        margin-left -.04rem
        font-size .24rem
</style>
