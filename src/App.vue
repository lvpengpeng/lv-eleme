<template>
  <div id="app">
    <router-link to="/goods">Go to goods</router-link>
    <router-link to="/ratings">Go to ratings</router-link>
    <router-link to="/seller">Go to seller</router-link>
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

</style>
