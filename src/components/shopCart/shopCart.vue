<template>
    <div class="shopCart">
      <div class="content">
        <div class="content-left">
          <div class="logo-wrapper">
            <div class="logo">
              <div class="icon-shopping_cart"></div>
            </div>
          </div>
          <div class="price">￥2</div>
          <div class="desc">另需配送费￥25元</div>
        </div>
        <div class="content-right">
          <div class="pay">￥10元起送</div>
        </div>
      </div>
    </div>
</template>

<script>
    export default {

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
          .logo-wrapper{
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
        }
      }
    }
</style>
