<template>
    <div class="control-content">
      <transition name="fadeRotate">
          <div class="cart-decrease " v-show="food.count>0"@click.stop.prevent="decreaseCart()"></div>
      </transition>
      <div class="cart-count"  v-show="food.count>0">{{food.count}}</div>
      <div class="cart-add"  @click="addCart"></div>
    </div>
</template>

<script>
  import  Vue from 'vue'
    export default {
      props:{
        food: {
          type:Object
        }
      },
      // created(){
      //   console.log(this.food)
      // },
      methods:{
        addCart(event){
          if(!event._constructed){
            return
          }

          if(!this.food.count){
            Vue.set(this.food,'count',1)
            //坑！！！！当给一个观测对象，添加一个他不存在的字段的时候，直接赋值是不可以的，检测不到属性的变化。所以需要引入vue，使用它的set接口。
            // this.food.count=1
          }else{
            this.food.count++
          }
          return this.food.count
        },
        decreaseCart() {
          if (!event._constructed || !this.food.count) {
            return
          }
          this.food.count--;
        }
      }
    }
</script>

<style scoped lang="scss">
    .control-content{
      height: 24px;
      display: flex;
      justify-content: space-between;
      .cart-decrease{
        display: inline-block;
        width: 24px;
        height: 24px;
        background:url("./img/减.png");
        background-size: cover;
        transition: all .4s linear;
        &.fadeRotate-enter-active, &.fadeRotate-leave-active{
          transform:translate3d(0,0,0) rotate(0);
        }
        &.fadeRotate-enter, &.fadeRotate-leave-active{
          /*opacity: 0*/
          transform :translate3d(24px,0,0) rotate(180deg);
        }
      }
      .cart-add{
        display: inline-block;
        width: 24px;
        height: 24px;
        background:url("./img/加.png");
        background-size: cover;
      }
      .cart-count{
        display: inline-block;
        line-height: 24px;
        font-size: 20px;
        width: 24px;
        text-align: center;
      }
      /*.inner{*/
        /*color:rgb(0,160,220)*/
      /*}*/
    }
</style>
