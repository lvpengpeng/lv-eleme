<template>
    <div class="goods">
      <div class="menu-wrapper">
          <ul>
            <li v-for="item in goods" class="menu-item">
              <span class="text">
                <span v-show="item.type>0" class="icon" :class="classMap[item.type]"></span>
                {{item.name}}
              </span>
            </li>
          </ul>
      </div>
      <div class="foods-wrapper">
        <ul>
          <li v-for="item in goods" class="food-list food-list-hook">
            <h1>{{item.name}}</h1>
            <ul>
              <!--@click="goDetail(food)"-->
              <li v-for="food in item.foods" class="food-item" >
                <div class="icon">
                  <img width="57" height="57" :src="food.icon"/>
                </div>
                <div class="content">
                  <h2>{{food.name}}</h2>
                  <p class="description" v-show="food.description">{{food.description}}</p>
                  <div class="sell-info">
                    <span class="sellCount">月售{{food.sellCount}}份</span>
                    <span class="rating">好评率{{food.rating}}%</span>
                  </div>
                  <div class="price">
                    <span class="newPrice"><span class="unit">￥</span>{{food.price}}</span>
                    <span v-show="food.oldPrice" class="oldPrice">￥{{food.oldPrice}}</span>
                  </div>
                  <div class="cartcontrol-wrapper">
                    <!--<cartcontrol :food="food"></cartcontrol>-->
                  </div>
                </div>
              </li>
            </ul>
          </li>
        </ul>
      </div>
    </div>
</template>

<script>
  import axios from 'axios'
    export default {
        props:{
         seller :{
            type:Object
          }
        },
      data (){
          return {
            goods :[]
          }
      },

      created() {
        this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee'];
        axios.get('/api/goods').then((response)=>{
          this.goods=response.data;
          console.log(this.goods,"axios.get('/api/goods').then((response)=>{22222222222222改成箭头函数，111111111不然this是undefined，数据也是undefined")
        })
          .catch((error)=> {
            console.log(error);
          });
      }
    }
</script>

<style scoped lang="scss">
.goods{
  display: flex;
  position: absolute;
  top: 140px;
  bottom: 46px;
  width: 100%;
  overflow:hidden;
  background: #ffffff;
  .menu-wrapper{
      /*flex:参数依次代表;等分，内容缩放，站位*/
    flex:0 0 80px;
    width: 80px;
    /*width如果不写在安卓手机有问题*/
    background:#cccccc;
    .menu-item{
      text-align: center;
      display: table;
      /*display: table;垂直居中最好的方法*/
      height: 54px;
      width: 56px;
      line-height: 14px;
      margin-left: 14px;
      .text{
        /*display: table-cell和vertical-align: middle;让内容垂直居中*/
        display: table-cell;
        width: 56px;
        vertical-align: middle;
        font-size: 12px;
        .icon {
          display: inline-block;
          vertical-align: top;
          width: 12px;
          height: 12px;
          margin-right: 4px;
          background-size: 12px 12px;
          background-repeat: no-repeat;
          &.decrease {
            background: url("./img/decrease_1@2x.png");
            background-size: cover;
          }
          &.discount {
            background: url("./img/discount_1@2x.png");
            background-size: cover;
          }
          &.guarantee {
            background: url("./img/guarantee_1@2x.png");
            background-size: cover;
          }
          &.invoice {
            background: url("./img/invoice_1@2x.png");
            background-size: cover;
          }
          &.special {
            background: url("./img/special_1@2x.png");
            background-size: cover;
          }
        }
      }
    }
  }
  .foods-wrapper{
    flex: 1;
    .food-list{
      h1{
        padding-left: 14px;
        height: 26px;
        line-height: 26px;
        border-left: 2px solid #d9dde1;
        font-size: 12px;
        color: rgb(147,153,159);
        background: #ddd;
      }
      .food-item{
        display: flex;
        margin: 18px;
        border-bottom: 1px solid #333;
        padding-bottom: 18px;
        &:last-child{
          border-bottom: 0;
          padding-bottom: 0;
        }
        .content{
          margin-left: 10px;
          .newPrice{
            font-size: 16px;
            color: red;
          }
        }
      }
    }
  }
}
</style>
