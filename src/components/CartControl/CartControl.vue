<template>
  <div class="cartcontrol">
    <transition>
    <div class="iconfont icon-remove" v-if="food.count" @click.stop="updataFoodCount(false)"></div>
    </transition>
    <div class="cart-count" v-if="food.count">{{food.count}}</div>
    <div class="iconfont icon-jia-tianchong" @click.stop="updataFoodCount(true)"></div>
  </div>
</template>

<script>
export default {
  props: {
    food: Object
  },
  methods:{
    updataFoodCount(isAdd){
      this.$store.dispatch('updataFoodCount', {isAdd,food:this.food});
    }
  }

};
</script>

<style lang="stylus" rel="stylesheet/stylus">
@import "../../common/stylus/mixins.styl"
.cartcontrol
  font-size: 0
  .cart-decrease
    display: inline-block
    padding: 6px
    line-height: 24px
    font-size: 24px
    color: rgb(0, 160, 220)

  .icon-remove
    display: inline-block
    padding 6px
    line-height 24px
    font-size 24px
    color $green
    &.move-enter-active, &.move-leave-active
      transition all 1s
    &.move-enter, &.move-leave-to
      opacity 0
      transform translateX(15px) rotate(180deg)
  .cart-count
    display: inline-block
    vertical-align: top
    width: 12px
    padding-top: 6px
    line-height: 24px
    text-align: center
    font-size: 10px
    color: rgb(147, 153, 159)
  .icon-jia-tianchong
    display: inline-block
    padding: 6px
    line-height: 24px
    font-size: 24px
    color $green
</style>
