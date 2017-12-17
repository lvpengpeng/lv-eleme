<template>
    <div class="goods">
      <div class="menu-wrapper">

      </div>
      <div class="foods-wrapper"></div>
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
  background: #cccccc;
  .menu-wrapper{
      /*flex:参数依次代表;等分，内容缩放，站位*/
    flex:0 0 80px;
    width: 80px;
    /*width如果不写在安卓手机有问题*/
    background:pink;
  }
  .foods-wrapper{
    flex: 1;
  }
}
</style>
