<template>
  <div id="app">
    <img src="./assets/logo.png">
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

<style scoped lang="stylus">
#app
  font-family 'Avenir' Helvetica Arial sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  margin-top 60px

</style>
