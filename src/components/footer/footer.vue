<template>
<div class="footer">
     <div class='bot-content'>
        <div class='content-left'>
          <div class='circle-out'>
            <span class='circle-in' :class="{'active':totalCount>0}">
              <i class='icon-shopping_cart'></i>
            </span>
            <div v-if='totalCount>0' class="num">{{totalCount}}</div>
          </div>
          <div class="price" :class="totalPrice>0?'active':''">
            ￥<output>{{totalPrice}}</output>
           
          </div>
           <div class="right-line">

            </div>
            <div class="send">另需配送费￥{{deliveryPrice}}元</div>
        </div>
        <div v-if='totalPrice==0' class='content-right'>
          ￥{{minPrice}}起送
        </div>
        <div v-else-if='totalPrice>0&&totalPrice<20' class='content-right'>
          还差￥{{20-totalPrice}}起送
        </div>
        <div v-else-if='totalPrice>=20' class="content-right mssend">
          立即下单
        </div>
    </div>
</div>
</template>
<script type="text/ecmascript-6">
export default {
  props: {
    selectFoods: {
      type: Array,
      default() {
        return [
          {
            price: 10,
            count: 2
          }
        ];
      }
    },
    deliveryPrice: {
      type: Number,
      default: 0
    },
    minPrice: {
      type: Number,
      default: 0
    }
  },
  data: function() {
    return {};
  },
  computed: {
    totalPrice() {
      let total = 0;
        console.log(this.selectFoods.length);
        this.selectFoods.forEach(food => {
          total += food.price * food.count;
        });
      return total;
    },
    totalCount() {
      let count = 0;
      this.selectFoods.forEach(food => {
        if (food.count) {
          console.log(1);
          count += food.count;
        }
      });
      return count;
    }
  },
  created() {
    // console.log(seller1.deliveryPrice);
  }
};
</script>
<style lang="stylus" rel="stylesheet/stylus">
.bot-content {
  height: 48px;
  width: 100%;
  line-height: 48px;
  background: #141d27;
  position: fixed;
  display: flex;
  bottom: 0;
  left: 0;

  .price {
    box-sizing: border-box;
    padding-left: 9px;
    padding-right: 6px;
    line-height: 48px;
    font-size: 16px;
    color: rgba(255, 255, 255, 0.4);
    font-weight: 700;
    height: 48px;
    float: left;

    &.active {
      color: #fff;
    }
  }

  .send {
    height: 48px;
    line-height: 48px;
    float: left;
    color: rgba(255, 255, 255, 0.4);
    margin-left: 6px;
    font-size: 12px;
  }

  .right-line {
    float: left;
    display: inline-block;
    height: 30px;
    margin-top: 9px;
    border-right: 1px solid rgba(255, 255, 255, 0.1);
  }

  .content-left {
    flex: 1;

    .circle-out {
      float: left;
      margin-top: -8px;
      margin-left: 9px;
      width: 50px;
      height: 50px;
      border-radius: 50%;
      background: #141d27;
      position: relative;

      .num {
        position: absolute;
        width: 24px;
        left: 30px;
        top: 0;
        font-size: 9px;
        font-weight: 700;
        color: #fff;
        line-height: 16px;
        height: 16px;
        background: rgb(240, 20, 20);
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
        border-radius: 40%;
        text-align: center;
      }

      .circle-in {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        display: inline-block;
        width: 42px;
        height: 42px;
        text-align: center;
        border-radius: 50%;
        background: rgba(255, 255, 255, 0.2);
        color: rgba(255, 255, 255, 0.4);
        line-height: 44px;
        font-size: 24px;

        &.active {
          background: rgb(8, 169, 228);
          color: #fff;
        }
      }
    }
  }

  .content-right {
    background: rgba(255, 255, 255, 0.1);
    width: 25%;
    text-align: center;
    box-sizing: border-box;
    height: 48px;
    line-height: 48px;
    font-size: 12px;
    font-weight: 700;
    color: rgba(255, 255, 255, 0.4);
    &.mssend{
    background #009736;
    color: #fff;
  }
  }
  
}
</style>
