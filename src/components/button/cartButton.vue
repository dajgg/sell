<template>
  <div class="button">
        <transition name='move'>
          <div class="cart-decrease " v-show="food.count>0" @click="plusCart">     
           <transition name="rotate">
              <span class="inner  icon-remove_circle_outline">    
              </span>
           </transition>     
          </div>
        </transition>
        <div class="cart-count" v-show="food.count>0">{{food.count}}</div>
        <div class="cart-add icon-add_circle" @click="addCart"></div>
  </div>
</template>
<script type="text/ecmascript-6">
import Vue from 'vue';
export default {
  props: {
    food: {
      type: Object
    }
  },
  created() {
    console.log(this.food);
  },
  methods: {
    addCart(event) {
      console.log(1);
      //   if (!event._constructed) {
      //     return ;
      //   }
      if (!this.food.count) {
        Vue.set(this.food, 'count', 1);
      } else {
        this.food.count++;
      }
      console.log(this.food.count);
    },
    plusCart(event) {
      if (this.food.count > 0) {
        this.food.count--;
      }
    }
  }
};
</script>

<style lang="stylus" rel="stylesheet/stylus">
.button {
  .cart-decrease {
    display: inline-block;
    padding: 6px;
    transition : all 3.5s linear;
    &.rotate-enter-active,&.move-leave{
      opacity: 1;
      transform: translate3D(0, 0, 0);
      
    }
      .inner {
          display: inline-block;
          line-height: 24px;
          font-size: 24px;
          color: rgb(0, 160, 220);
          transition: all .5s linear;
        }
   &.move-enter ,&.move-leave-active{
      opacity: 0;
      transform: translate3D(24px, 0, 0); 
      }
   // &.move-enter ,&.move-leave-active .inner{
   //   transform : rotate(180deg)
   // }
    }
  .cart-count {
    display: inline-block;
    font-size: 10px;
    line-height: 24px;
    vertical-align: top;
    width: 12px;
    padding-top: 6px;
    text-align: center;
    color: rgb(147, 153, 159);
  }
  .cart-add {
    display: inline-block;
    padding: 6px;
    line-height: 24px;
    font-size: 24px;
    color: rgb(0, 160, 220);
  }
}
</style>
