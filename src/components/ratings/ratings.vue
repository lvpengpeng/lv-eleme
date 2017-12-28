<template>
    <div class="ratings" ref="ratingsWrapper">
      <div class="ratings-warp">
        <div class="overview">
          <div class="overview-left">
            <h1>4.2</h1>
            <div class="title">综合评分</div>
            <div class="rank">高于周边商家92.6%</div>
          </div>
          <div class="overview-rigth">
            <div class="score-wrapper">
              <span>服务态度</span>
            </div>
            <div class="score-wrapper">
              <span>商品评分</span>
            </div>
            <div class="delivery-wrapper">
              <div>送达时间</div>
              <div>36分钟</div>
            </div>
          </div>
        </div>
        <div class="split"></div>
        <div class="ratingselect">
          <ul class="select-box">
            <li class="n1">全部</li>
            <li class="n2">满意</li>
            <li class="n3">不满意</li>
          </ul>
          <div class="toggle">
            <em class="icon-ok2"></em>
            <span>只看有评论的内容</span>
          </div>
        </div>
        <div class="evel-list">
          <ul>
            <li class="evel" >
              <div class="avatar">
                <img  width="28" height="28">
              </div>
              <div class="content">
                  <h4 class="name">3******c</h4>
                  <div class="start">4颗星</div>
                  <div class="text">不错,粥很好喝,我经常吃这一家,非常赞,以后也会常来吃,强烈推荐.</div>
                  <div class="zan-title">
                    <em class="zan"></em>
                    <ul class="title">
                      <li>123</li>
                      <li>41</li>
                      <li>rere</li>
                      <li>41</li>
                      <li>rere</li>
                      <li>rere</li>
                    </ul>
                    <div class="time">12:16</div>
                  </div>
              </div>
            </li>
            <li class="evel" >
              <div class="avatar">
                <img  width="28" height="28">
              </div>
              <div class="content">
                <h4 class="name">3******c</h4>
                <div class="start">3颗星</div>
                <div class="text">不错,粥很好喝,我经常吃这一家,非常赞,以后也会常来吃,强烈推荐.</div>
                <div class="zan-title">
                  <em class="zan"></em>
                  <ul class="title">
                    <li>123</li>
                    <li>41</li>
                    <li>rere</li>
                    <li>41</li>
                    <li>rere</li>
                    <li>rere</li>
                  </ul>
                  <div class="time">12:16</div>
                </div>
              </div>
            </li>
            <li class="evel" >
            <div class="avatar">
              <img  width="28" height="28">
            </div>
            <div class="content">
              <h4 class="name">3******c</h4>
              <div class="start">5颗星</div>
              <div class="text">不错,粥很好喝,我经常吃这一家,非常赞,以后也会常来吃,强烈推荐.</div>
              <div class="zan-title">
                <em class="zan"></em>
                <ul class="title">
                  <li>123</li>
                  <li>41</li>
                  <li>rere</li>
                  <li>41</li>
                  <li>rere</li>
                  <li>rere</li>
                </ul>
                <div class="time">12:16</div>
              </div>
            </div>
          </li>

          </ul>
        </div>
      </div>
    </div>
</template>

<script>
  import  BScrool from  'better-scroll'
    export default {
      created(){
          this._initScroll()
        },
      methods:{
        _initScroll(){
          this.$nextTick(() => {
            this.ratingsScrool = new BScrool(this.$refs.ratingsWrapper, {});
          })
        }
    }
  }
</script>

<style scoped lang="scss">
.ratings{
  position: absolute;
  top: 130px;
  bottom: 0;
  left: 0;
  width: 100%;
  overflow: hidden;
  .ratings-warp{
    .overview{
      padding: 18px 0;
      display: flex;
      .overview-left{
        width: 137px;
        text-align: center;
        border-right: 1px solid rgba(7,17,27,0.1);
        padding: 6px 0;
        h1{
          margin-bottom: 6px;
          line-height: 28px;
          font-size: 24px;
          color: #f90;
        }
        .title{
          margin-bottom: 8px;
          line-height: 12px;
          font-size: 12px;
          color: #07111b;
        }
        .rank{
          line-height: 10px;
          font-size: 10px;
          color: #93999f;
        }
      }
      .overview-rigth{
        flex: 1;
        padding: 6px 0 6px 24px;
        .score-wrapper{
          display: flex;
          margin-bottom: 8px;
        }
        .delivery-wrapper{
          display: flex;
          div:nth-child(2){
            margin-left: 0.62rem;
            color: #93999f;
          }
        }
      }
    }
    .split{
      width: 100%;
      height: 16px;
      border-top: 1px solid rgba(7,17,27,0.1);
      border-bottom: 1px solid rgba(7,17,27,0.1);
      background: #f3f5f7;
    }
    .ratingselect{
      background:#fff;
      padding: 0 18px;
      border-bottom: 1px solid #cccccc;
      .select-box{
        width: 100%;
        border-bottom: 1px solid #cccccc;
        display: flex;
        padding:18px 0;
        li{
          padding: 8px 12px;
          margin-right: 8px;
        }
        .n1{
          background: #00a0dc;
        }
        .n2{
          background:rgba(0,160,220,0.2);
        }
        .n3{
          background:rgba(77,85,93,0.2);
        }
      }
      .toggle{
        width: 100%;
        padding: 8px 0;
        display: flex;
        align-items: center;
        em{
          display: inline-block;
          width: 24px;
          height: 24px;
          background: red;
          margin-right: .4rem;
        };
        .icon-ok{
          background: url("./img/icon_ok.png");
          background-size: cover;
        }
        .icon-ok2{
          background: url("./img/icon_ok2.png");
          background-size: cover;
        }
        span{
          font-size: .24rem;
        }
      }
    }

  }
  .evel-list{
    .evel{
      display:flex;
      padding :18px 0;
      margin :0 18px;
      border-bottom :1px solid rgba(7,17,27,0.1);
      .avatar{
        flex :0 0 28px;
        margin-right: 6px;
      }
      .content{
        position: relative;
        flex :1;
        .name{
          width: 100%;
          height: 22px;
        }
        .start{
          width: 100%;
          height: 22px;
        }
        .text{
        }
        .zan-title{
          display: flex;
          .zan{
            display: inline-block;
            width: 20px;
            height: 20px;
            background: url("./img/赞.png");
            background-size: cover;
            margin-right: 6px;
          }
          .title {
            flex: 1;
             li{
              display: inline-block;
              width: 40px;
              height: 20px;
              line-height: 20px;
              text-align: center;
              background: rgba(1,1,1,.3);
              margin: 0 6px 6px 0;
               border: 1px solid #cccccc;
               border-radius: 20px;
            }
          }
          .time{
            position: absolute;
            right: 0;
            top: 0;
          }
        }
      }
    }
  }
}
</style>
