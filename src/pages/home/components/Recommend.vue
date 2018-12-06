<template>
  <div>
    <div class='title'>热销推荐</div>
    <ul>
      <router-link
        tag='li'
        class='item border-bottom'
        v-for="item of list"
        :key="item.id"
        :to="'/detail/' + item.id"
      >
        <img class='item-img' :src='item.imgUrl'/>
        <div class='item-info'>
          <p class='item-title'>{{item.title}}</p>
          <p class='item-desc'>{{item.desc}}</p>
          <button class='item-btn'>查看详情</button>
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

<style lang='stylus' scoped>
@import '~styles/mixins.styl'
  .title
    margin-top: .1rem
    line-height: .8rem
    background: #eee
    text-indent: .2rem
  .item
    overflow: hidden
    height: 1.9rem
    //background: #ccc
    .item-img
      float: left
      padding: 0.1rem
      width: 1.7rem
      height: 1.7rem
    .item-info
      min-width: 0
      margin-left: 2rem
      //background: red
      margin-top: .2rem
      .item-title
        line-height: .54rem
        font-size: .32rem
        ellipsis()
      .item-desc
        line-height: .4rem
        color: #cccccc
        ellipsis()
      .item-btn
        line-height: .44rem
        margin-top: .16rem
        background: #ff9300
        padding: 0 .2rem
        border-radius: .06rem
        color: #fff
</style>
