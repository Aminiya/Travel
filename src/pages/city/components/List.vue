<template>
  <div class='list' ref='wrapper'>
    <div>
      <div class='area'>
        <div class='title border-topbottom'>当前城市</div>
        <div class='button-list'>
          <div class='button-wrapper'>
            <div class='button'>{{this.currentCity}}</div>
          </div>
        </div>
      </div>
      <div class='area'>
        <div class='title border-topbottom'>热门城市</div>
        <div class='button-list'>
          <div
            class='button-wrapper'
            v-for = "item of hotCities"
            :key = item.id
            @click = 'handleCityChange(item.name)'
          >
            <div class='button'>{{item.name}}</div>
          </div>
        </div>
      </div>
      <div
        class='area'
        v-for = '(item, key) of cities'
        :key = key
        :ref = key
      >
        <div class='title border-topbottom'>{{key}}</div>
        <div class='item-list'>
          <div
            class='item border-bottom'
            v-for = '(innerItem, index) of item'
            :key = index
            @click = 'handleCityChange(innerItem.name)'
          >
            {{innerItem.name}}
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
    ...mapState({currentCity: 'city'})
  },
  methods: {
    handleCityChange: function (city) {
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>

<style lang='stylus' scoped>
  @import '~styles/variables.styl'
  .border-topbottom
    &:before
      border-color: #cccccc
    &:after
      border-color: #cccccc
  .border-bottom
    &:before
      border-color: #ccc
  .list
    position: absolute
    top: 1.58rem
    bottom: 0
    left: 0
    right: 0
    overflow: hidden
    .title
      line-height: .54rem
      background: #eeeeee
      font-size: .26rem
      padding-left: .2rem
      color: #666
    .button-list
      overflow: hidden
      padding: .1rem .6rem .1rem .1rem
      .button-wrapper
        box-sizing: border-box
        width: 33.3%
        float: left
        padding: .2rem .2rem .1rem .2rem
        .button
          line-height: .46rem
          border: .02rem solid #cccccc
          border-radius: .06rem
          text-align: center
    .item-list
      .item
        padding: 0 .2rem
        line-height: .76rem
        color: #666
</style>
