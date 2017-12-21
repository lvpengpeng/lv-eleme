<template>
    <div class="shopCart">
      <div class="content">
        <div class="content-left">
          <div class="logo-wrapper">
            <div class="logo">
              <div class="icon-shopping_cart">
                <span  v-show="totalCount>0">{{totalCount}}</span>
              </div>
            </div>
          </div>
          <div class="price highLight" :class="{highLight:totalCount>0}">￥{{totalPrice}}</div>
          <div class="desc">另需要配送费￥{{deliveryPrice}}元</div>
        </div>
        <div class="content-right">
          <div class="pay" :class="{'enough':totalPrice>=minPrice}"> {{payDesc}}</div>
        </div>
      </div>
    </div>
</template>

<script>

    export default {
      props:{
        selectFoods:{
          type:Array,
          default() {
            return [
              // {price:10,count:1} 模拟有一物品，如果父组件没有selectFoods，就现实这么默认的了。
              ]
          }
        },
        minPrice:{
          type:Number,
          default:0
        },
        deliveryPrice:{
          type:Number,
          default:2
        }
      },
      // watch: {
      //   selectFoods (val) {
      //     console.log(val, '11999');
      //   }
      // },
      created(){

      },
      computed:{
        totalCount() {
          console.log(this.selectFoods,222)
          let count = 0
          this.selectFoods.forEach((food) => {
            count += food.count
          })
          return count
        },
        totalPrice() {
          let total = 0
          this.selectFoods.forEach((food) => {
            if (food.count) {
              total += food.price * food.count
            }
          })
          return total
        },
        payDesc(){
          let diff = this.minPrice - this.totalPrice
          if (!this.totalPrice) {
            return `￥${this.totalPrice}起送`
          } else if (diff > 0) {
            return `还差￥${diff}元`
          } else {
            return '去结算'
          }
        }
      }
    }
</script>

<style scoped lang="scss">
    .shopCart{
      position:fixed;
      height: 46px;
      width: 100%;
      bottom:0;
      left: 0;
      background:rgba(3,3,3,.4);
      .content{
        display: flex;
        .content-left{
          flex: 1;
          span{
            vertical-align: top;
            display: inline-block;
          }
          .highLight{
            color: yellow;
          }
          .logo-wrapper{
            position: relative;
            display: inline-block;
            vertical-align: top;
            /*.让price和.logo-wrapper和desc都是一行并列，把他们转成（display: inline-block;）行内块，之后统一（vertical-align: top）顶对齐就Ok了*/
            width: 56px;
            height: 56px;
            background: pink;
            margin: 0 12px;
            position: relative;
            top: -10px;
            padding: 6px;
            background: #333;
            -webkit-border-radius: 50%;
            -moz-border-radius: 50%;
            border-radius: 50%;
            /*可通过将 box-sizing 设置为 "border-box"。这可令浏览器呈现出带有指定宽度和高度的框，并把边框和内边距放入框中。*/
            box-sizing: border-box;
            .logo{
              width:100%;
              height: 100%;
              -webkit-border-radius: 50%;
              -moz-border-radius: 50%;
              border-radius: 50%;
              background: yellow;
              display: flex;
              justify-content: center;
              align-items: center;
              .icon-shopping_cart{
                width: 28px;
                height:28px;
                background: url("./images/cart.png");
                background-size: cover;
                span{
                  width:40px;
                  height: 22px;
                  border-radius:22px;
                  background: red;
                  position: absolute;
                  right: -25%;
                  top: 0;
                  text-align: center;
                  line-height: 22px;
                }
              }
            }
          }
          .price{
            display: inline-block;
            vertical-align: top;
            margin-top: 12px;
            line-height: 24px;
            font-size: 16px;
            font-weight: 700;
            padding-right: 12px;
            box-sizing: border-box;
            border-right: 1px solid #ffffff;
          }
          .desc{
            display: inline-block;
            vertical-align: top;
            margin: 12px 0 0 12px;
            line-height: 24px;
            font-size: 10px;
          }
        }
        .content-right{
          flex: 0 0 105px;
          .pay{
            width: 100%;
            background: #666;
            height: 48px;
            line-height: 48px;
            text-align: center;
            font-size: 12px;
            font-weight: 700;
          }
          .enough{
            background: aqua;
            color: blue;
          }
        }
      }
    }
</style>
