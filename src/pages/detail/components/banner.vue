<template>
  <div>
    <div class='banner' @click = 'handleBannerClick'>
      <img class='banner-img' :src = 'bannerImg'/>
      <div class='banner-infor'>
        <div class='banner-title'>
          {{this.sightName}}
        </div>
        <div class='banner-number'>
          <span class="iconfont banner-icon">&#xe650;</span>
          {{this.gallaryImgs.length}}
        </div>
      </div>
    </div>
    <fade-animation>
      <common-gallary
        :imgs = 'gallaryImgs'
        v-show = 'showSwiper'
        @close = 'handleGallaryClose'
      ></common-gallary>
    </fade-animation>
  </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/fade/FadeAnimation'
export default {
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImg: String,
    gallaryImgs: Array
  },
  data () {
    return {
      showSwiper: false
    }
  },
  components: {
    CommonGallary,
    FadeAnimation
  },
  methods: {
    handleBannerClick: function () {
      this.showSwiper = true
    },
    handleGallaryClose () {
      this.showSwiper = false
    }
  }
}
</script>

<style lang='stylus' scoped>
  .banner
    height: 0
    padding-bottom: 55%
    .banner-img
      width: 100%
    .banner-infor
      display:flex
      position: absolute
      margin-top: -.8rem
      width: 100%
      color: #ffffff
      padding-left: .2rem
      background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, .8))
      .banner-title
        flex: 1
        font-size: .32rem
        margin: .2rem 0
      .banner-number
        margin: .2rem 0
        padding: 0 .4rem
        height: .4rem
        line-height: .4rem
        border-radius: .2rem
        background: rgba(0, 0, 0, .8)
        font-size: .24rem
        .banner-icon
          font-size: .24rem
</style>
