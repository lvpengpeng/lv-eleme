<template>
    <div class="goods">
      <div class="menu-wrapper" ref="menuWrapper" >
          <ul>
            <li v-for="(item ,index) in goods" @click="menuClick(index,$event)" :class="index==menuCurrentIndex?'menu-item-selected':'menu-item'">
              <span class="text">
                <span v-show="item.type>0" class="icon" :class="classMap[item.type]"></span>
                {{item.name}}
              </span>
            </li>
          </ul>
      </div>
      <div class="foods-wrapper" ref="foodsWrapper" >
        <ul>
          <!--如果用js控制元素，最好单独添加一个class，这个class没有样式，就只赋值js部分，通常后缀名food-list-hook-->
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
  import  BScrool from  'better-scroll'
    export default {
        props:{
         seller :{
            type:Object
          }
        },
      data (){
          return {
            goods :[],
            listHeight:[],
            foodsScrollY: 0
          }
      },

      created() {
        this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee'];
        axios.get('/api/goods').then((response)=>{
          this.goods=response.data;
          console.log(this.goods,"axios.get('/api/goods').then((response)=>{22222222222222改成箭头函数，111111111不然this是undefined，数据也是undefined")
        this.$nextTick(()=>{
          // 把this._initScroll()放在this.$nextTick函数里，是因为由于异步原因vue里改变数据后，dom没有变化。所以放在this.$nextTick方法里，当nextTick的时候，初始化_initScroll()
          this._initScroll()
          this._calculateHeight()
        })
        })
          .catch((error)=> {
            console.log(error);
          });
      },
      methods:{
          _initScroll(){
            this.menuScrool = new BScrool(this.$refs.menuWrapper,{
            click:true
            //click:true是让滚动区域可点击，不然事件不能调用
            });

            this.foodsScrool = new BScrool(this.$refs.foodsWrapper,{
              click:true,
              //click:true是让滚动区域可点击，不然事件不能调用
              probeType: 3
            });

            // 监控滚动事件
            this.foodsScrool.on('scroll', (pos) => {
              this.foodsScrollY = Math.abs(Math.round(pos.y))
            })
          },
        _calculateHeight(){
          let foodList = this.$refs.foodsWrapper.querySelectorAll('.food-list-hook');
          let height = 0
          this.listHeight.push(height)
          for (let i = 0, l = foodList.length; i < l; i++) {
            let item = foodList[i]
            height += item.clientHeight
            this.listHeight.push(height)
          }
//          console.log(this.listHeight,2222)
        },

        menuClick(index, event){
//          console.log(index,event)
          if (!event._constructed) {
            return
          }
          this.foodsScrool.scrollTo(0, -this.listHeight[index], 300)
        }
      },
      computed:{
        menuCurrentIndex() {
          for (let i = 0, l = this.listHeight.length; i < l; i++) {
            let topHeight = this.listHeight[i]
            let bottomHeight = this.listHeight[i + 1]
            if (!bottomHeight || (this.foodsScrollY >= topHeight && this.foodsScrollY < bottomHeight)) {
              return i
            }
          }
          return 0
        }
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
    .menu-item-selected,.menu-item{
      text-align: center;
      display: table;
      /*display: table;垂直居中最好的方法*/
      height: 54px;
      width: 52px;
      line-height: 14px;
      padding: 0 14px;
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
    .menu-item-selected{
      background:#fff;

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
        margin: 18px 18px 0 18px;
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
