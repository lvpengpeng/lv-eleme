<template>
  <div id="app">
    <div class="tab">
      <div class="tab-item">
        <router-link to="/goods">商品</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings">评论</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link>
      </div>
    </div>
    <router-view/>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'app',
  data (){
    return {
      goods:""
    }
  },
  created() {
        axios.get('/api/goods').then((response)=>{
            this.goods=response.data;
            console.log(this.goods,"axios.get('/api/goods').then((response)=>{改成箭头函数，不然this是undefined，数据也是undefined")
          })
          .catch((error)=> {
              console.log(error);
            });
      }
}
</script>

<style scoped lang="scss">
  .tab{
    display: flex;
    height: 40px;
    line-height: 40px;
    width: 100%;
    .tab-item{
      flex: 1;
      text-align: center;
      a{
        display:block;
        font-size:14px;
        &.active{
          font-size:14px;
          color:blue
        }
      }
    }
  }
</style>
