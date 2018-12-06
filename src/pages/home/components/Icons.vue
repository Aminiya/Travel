<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for = "(page, index) of pages" :key = "index">
        <div
          class = "icon"
          v-for = "item of page"
          :key = "item.id"
        >
          <div class="icon-img">
            <img class="icon-img-content" :src='item.imgUrl' />
          </div>
          <p class="icon-desc">{{item.desc}}</p>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        autoplay: false
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)
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
@import '~styles/variables.styl'
@import '~styles/mixins.styl'
  .icons >>> .swiper-container
    height: 0
    padding-bottom: 50%
    .icon
      float: left
      height: 0
      width: 25%
      padding-bottom: 25%
      overflow: hidden
      .icon-img
        width: 100%
        height: 0
        padding-bottom: 70%
        margin-top: 10%
        overflow: hidden
        /* position: absolute
        margin-top: 0
        margin-left: 0
        margin-right: 0
        margin-bottom: .44rem */
        .icon-img-content
          width: 65%
          display: block
          margin: 0 auto
      .icon-desc
        text-align: center
        color: $darkTextColor
        ellipsis()
</style>
