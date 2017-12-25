<template>
  <div class="seller" ref="sellerWrapper">
    <!--使用better-scroll的时候，在seller获取真实的dom滚动。seller下面的子集必须是一个元素，所以使用seller-content包一下。-->
    <div class="seller-content" >
      <div class="overview">
        <h1 class="title">粥品香坊（回龙观）</h1>
        <div class="desc ">
          <div>start</div>
          <span>(24)</span>
          <span>月销90单</span>
          <div class="xin">
            <div class="xin-icon"></div>
            <div>收藏</div>
          </div>
        </div>
        <ul class="remark">
          <li>
            <h2>11</h2>
            <span>22</span>分钟
          </li>
          <li>
            <h2>22</h2>
            <span>33</span>分钟
          </li>
          <li>
            <h2>33</h2>
            <span>3</span>分钟
          </li>
        </ul>
      </div>
      <div class="split"></div>
      <div class="bulletin">
        <h1>公告与活动</h1>
        <div class="content-wrapper">
          <p>粥品香坊其烹饪粥料的秘方源于中国千年古法，在融和现代制作工艺，由世界烹饪大师屈浩先生领衔研发。坚守纯天然、0添加的良心品质深得消费者青睐，发展至今成为粥类的引领品牌。是2008年奥运会和2013年园博会指定餐饮服务商。</p>
        </div>
        <ul class="supports">
          <li class="support-item">
            <span></span>
            <div>在线支付满28减5</div>
          </li>
          <li class="support-item">
            <span></span>
            <div>在线支付满28减5</div>
          </li>
          <li class="support-item">
            <span></span>
            <div>在线支付满28减5</div>
          </li>
        </ul>
      </div>
      <div class="split"></div>
      <div class="pics">
        <h2 class="title">商家实景</h2>
        <div class="pic-wrapper">
          <ul></ul>
        </div>
      </div>
      <div class="split"></div>
      <div class="info">
        <h2 class="title">商家信息</h2>
        <ul>
          <li class="info-item">营业时间:10:00-20:30</li>
          <li class="info-item">营业时间:10:00-20:30</li>
          <li class="info-item">营业时间:10:00-20:30</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
  import BScroll from 'better-scroll'
    export default {
      created() {
               this._inits()
            },
          methods: {
            _inits() {
                this.$nextTick(() => {
                  this.sellerScroll = new BScroll(this.$refs.sellerWrapper)
                })

            }
          }
    }
</script>

<style scoped lang="scss">
  .seller{
    position: absolute;
    top: 174px;
    bottom: 0;
    left: 0;
    width: 100%;
    overflow: hidden;
    .seller-content{
      .overview{
        padding: 18px;
        h1{
          margin-bottom: 8px;
          line-height: 4px;
          color: #07111b;
          font-size: 14px;
        }
        .desc{
          display: flex;
          padding-bottom: 18px;
          border-bottom: 1px solid #cccccc;
          span{
            display: inline-block;
            margin-right: 12px;
            line-height: 18px;
            vertical-align: top;
            font-size: 10px;
            color: #4d555d;
          }
          .xin{
            width: 50px;
            position:absolute;
            right: 38px;
            margin-top: -20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            .xin-icon{
              width: 20px;
              height: 20px;
              background: url("./img/未收藏.png");
              background-size: cover;
            }
          }
          }
        .remark{
          display: flex;
          text-align: center;
          padding-top: 12px;
          li{
            flex: 1;
            border-right:#ccc;
            h2{
              margin-bottom: 4px;
              line-height: 10px;
              font-size: 10px;
              color: #93999f;
            }
            span{
              font-size: 24px;
            }
          };
        }
        }
      .split{
        width: 100%;
        height: 20px;
        background: #f3f5f7;
        border-top: 1px solid rgba(7,17,27,0.1);
        border-bottom: 1px solid rgba(7,17,27,0.1);
      }
      .bulletin{
        padding: 18px 18px 0 18px;
        h1{
          margin-bottom: 8px;
          line-height: 14px;
          color: #07111b;
          font-size: 14px;
        }
        .content-wrapper{
          padding: 0 12px 16px 12px;
          position: relative;
          p{
            line-height: 24px;
            font-size: 12px;
            color: #f01414;
          }
        }
        .supports{
          width: 100%;
          .support-item{
            border-top: 1px solid #cccccc;
            padding: 16px 12px;
            display: flex;
            align-items: center;
            height: 16px;
            span{
              width: 12px;
              height: 12px;
              background: red;
            line-height: 16px;
            }
            div{
              line-height: 16px;
              font-size: 12px;
              color: #07111b;
              margin-left: 6px;
            }
          }
        }
      }
      .pics{
        padding: 18px;
        h2{
          margin-bottom: 12px;
          line-height: 14px;
          color: #07111b;
          font-size: 14px;
        }
        .pic-wrapper{
          width: 100%;
          height: 90px;
          background: #666;
        }
      }
      .info{
        padding: 18px 18px 0 18px;
        color: #07111b;
        .title{
          padding-bottom: 12px;
          line-height: 14px;
          font-size: 14px;
        }
        .info-item{
          padding: 16px 12px;
          line-height: 16px;
          font-size: 12px;
          border-top: 1px solid #cccccc;
        }
      }
    }
  }
</style>
