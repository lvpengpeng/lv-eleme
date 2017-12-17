<template>
    <div class="header">
      <div class="content-wrapper">
        <div class="avatar">
          <img :src="seller.avatar" width="64" height="64" />
        </div>
        <div class="content">
          <div class="title">
            <span class="brand"></span>
            <span class="name">{{seller.name}}</span>
          </div>
          <div class="description">
            {{seller.description + ' / ' + seller.deliveryTime + '分钟送达'}}
          </div>
          <div class="supports" v-if="seller.supports">
            <div class="supports_desc">
              <span class="icon" :class="iconClassMap[seller.supports[0].type]"></span>
              <span class="text">{{seller.supports[0].description}}</span>
            </div>

          </div>
          <div class="support-count" v-if="seller.supports" @click="showDetails()">
            <span class="count">{{seller.supports.length+'个'}}</span>
            <i class="icon-keyboard_arrow_right"></i>
          </div>
        </div>
      </div>
      <div class="background">
        <img :src="seller.avatar" alt="">
      </div>
      <transition name="fade">
      <div v-show="detailShow" class="detail">
          <div class="detail-wrapper clearfix">
            <div class="datail-main">
              《步步惊人的命运，却无法掌握自己的结局，个人情感夹杂在争斗的惨烈中备受煎熬。经历几番爱恨嗔痴
              ，身心俱疲的故事。《步步惊心》是2005年网上连载的穿越小说，作者是桐华。[1]  该小说主要讲述了现
              为满族少女马尔泰·若曦，身不由己地卷入“九子夺嫡”的纷争。她看透所有人的命运，却无法掌握自己k
          </div>
          </div>
        <div class="detail-close">
          <i class="icon-close" @click="hideDetail()">close</i>
        </div>
      </div>
      </transition>
    </div>
</template>

<script>
    export default {
      props: {
        seller: {
          type: Object
        }
      },
      data (){
        return {
          detailShow:false
        }
      },
      created() {
        this.iconClassMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee']
      },
      methods:{
        showDetails(){
         this.detailShow=true
        },
        hideDetail(){
          this.detailShow=false
        }
      }
    }
</script>

<style scoped lang="scss">
  .header {
    width: 100%;
    height: 100px;
    position: relative;
    overflow: hidden;
    .background{
      width: 100%;
      height: 100%;
      position: absolute;
      z-index: -1;
      left: 0;
      top: 0;
      background: rgba(225,225,225,0.5);
      filter:blur(10px);
      img{
        width: 100%;
        height: 100%;
        position: absolute;
        backdrop-filter:blur(10px);
        left: 0;
        top: 0;
      }
    }
    .content-wrapper {
      padding: 20px;
      display: flex;
      .avatar {
      }
    }
    .content {
      margin-left: 10px;
      .title {
        .brand {
          display: inline-block;
          vertical-align: top;
          width: 30px;
          height: 18px;
          background: url("./img/brand@2x.png");
          background-size: cover;
        }
        .name {

        }
      }
      .description {
        font-size: 12px;
        margin-bottom: 10px;
      }
      .supports {
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
        .text {
          line-height: 12px;
          font-size: 10px;
        }
      }
      .support-count {
        position: absolute;
        right: 12px;
        bottom: 20px;
        padding: 0 8px;
        height: 24px;
        line-height: 24px;
        border-radius: 14px;
        background-color: rgba(0, 0, 0, 0.2);
        text-align: center;
        .count {
          vertical-align: top;
          font-size: 10px;
        }
        .icon-keyboard_arrow_right{
          font-size:10px;
          margin-left :2px ;
          line-height: 24px;
        }
      }
    }
    .detail{
      width: 100%;
      height: 100%;
      position: fixed;
      left: 0;
      top:0;
      z-index:100;
      background: rgba(3,2,1,0.8);
      overflow: auto;
      .detail-wrapper{
        width: 100%;
        min-height: 100%;overflow: hidden;
        .datail-main{
          margin-top: 64px;
          padding-bottom: 64px;margin-bottom: 20px;
          color: #fff
        }
      }
      .detail-close{
        margin: -64px auto 0;
        clear:both;
        .icon-close{
          width: 100px;
          height: 40px;
          line-height: 40px;
          text-align: center;
          display: block;
          margin: 0 auto;
          background: yellow;
        }
      }
    }
    .fade-enter-active, .fade-leave-active {
      transition: opacity .5s
    }
    .fade-enter, .fade-leave-to /* .fade-leave-active in below version 2.1.8 */ {
      opacity: 0
    }
  }
</style>
