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
    </div>
</template>

<script>
    export default {
      props: {
        seller: {
          type: Object
        }
      },
      created() {
        this.iconClassMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee']
      },
      methods:{
        showDetails(){
          alert(2)
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
  }




</style>
