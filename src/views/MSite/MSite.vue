<template >
  <div class="msite">
    <!-- 首页头部内容 -->
    <HeaderTop :title="address.name">
      <span class="header_search" slot="left">
        <i class="iconfont icon-sousuo"></i>
      </span>
      <span class="header_login" slot="right">
        <span class="header_login_text">登录|注册</span>
      </span>
    </HeaderTop>
    <!-- 首页导航 -->
    <div class="msite_nav">
          <div class="swiper-container">
            <div class="swiper-wrapper">
              <div class="swiper-slide">
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/1.jpg">
                  </div>
                  <span>甜品饮品</span>
                </a>
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/2.jpg">
                  </div>
                  <span>商超便利</span>
                </a>
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/3.jpg">
                  </div>
                  <span>美食</span>
                </a>
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/4.jpg">
                  </div>
                  <span>简餐</span>
                </a>
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/5.jpg">
                  </div>
                  <span>新店特惠</span>
                </a>
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/6.jpg">
                  </div>
                  <span>准时达</span>
                </a>
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/7.jpg">
                  </div>
                  <span>预订早餐</span>
                </a>
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/8.jpg">
                  </div>
                  <span>土豪推荐</span>
                </a>
              </div>
              <div class="swiper-slide">
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/9.jpg">
                  </div>
                  <span>甜品饮品</span>
                </a>
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/10.jpg">
                  </div>
                  <span>商超便利</span>
                </a>
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/11.jpg">
                  </div>
                  <span>美食</span>
                </a>
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/12.jpg">
                  </div>
                  <span>简餐</span>
                </a>
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/13.jpg">
                  </div>
                  <span>新店特惠</span>
                </a>
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/14.jpg">
                  </div>
                  <span>准时达</span>
                </a>
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/1.jpg">
                  </div>
                  <span>预订早餐</span>
                </a>
                <a href="javascript:" class="link_to_food">
                  <div class="food_container">
                    <img src="./images/nav/2.jpg">
                  </div>
                  <span>土豪推荐</span>
                </a>
              </div>
            </div>
            <!-- swiper 分页器 -->
            <div class="swiper-pagination"></div>
          </div>
    </div>
    <!--首页附近商家-->
    <div class="msite_shop_list">
      <div class="shop_header">
        <i class="iconfont icon-xuanxiang"></i>
        <span class="shop_header_title">附近商家</span>
      </div>
      <ShopList></ShopList>
    </div>
  </div>
</template>
<script>
import { mapState } from 'vuex'
import Swiper from 'swiper'
import 'swiper/swiper.min.css'
import HeaderTop from '../../components/HeaderTop/HeaderTop.vue'
import ShopList from '../../components/ShopList/ShopList.vue'
export default {
  mounted () {
    this.$store.dispatch('getCategorys')
    // 创建一个Swiper实例对象 ，实现轮播效果
    /* eslint-disable no-new */
    new Swiper('.swiper-container', {
      loop: true, // 可以循环轮播
      // 如果需要分页器
      pagination: {
        el: '.swiper-pagination'
      }

    })
  },
  computed: {
    // 数据读取
    ...mapState(['address', 'categorys'])
  },
  components: {
    HeaderTop,
    ShopList
  }
}
</script>

<style lang="less" scoped>
.msite{
  width: 100%;

  .msite_nav{
      margin-top:45px;
      height: 200px;
      background: #fff;
      position: relative;
      &::before{
        // 一像素下边框
        content:'';
        position :absolute;
        z-index: 200;
        left: 0;
        bottom :0;
        width :100%;
        height :1px;
        background-color: #e4e4e4;
        transform :scaleY(0.5);
      }
      .swiper-container{
        width: 100%;
        height: 100%;
        .swiper-wrapper{
          width: 100%;
          height: 100%;
          .swiper-slide{
            display: flex;
            justify-content: center;
            align-items: flex-start;
            flex-wrap:wrap;
            .link_to_food{
              width: 25%;
              .food_container{
                display: block;
                width: 100%;
                text-align: center;
                padding-bottom:10px;
                font-size: 0;
                img{
                  display: inline-block;
                  width: 50%;
                  height: 50%;
                }
              }
              span{
                display: block;
                width: 100%;
                text-align: center;
                font-size: 13px;
                color: #666;
              }
            }
          }
        }
        .swiper-pagination{
          background: #02a774;
        }
      }
  }
  .msite_shop_list{
    position:relative;
    margin-top: 10px;
    background:#fff;
    &::before{
      content: '';
      position :absolute;
      z-index :200;
      left: 0;
      top: 0;
      width :100%;
      height: 1px;
      background: #e4e4e4;
    }
    .shop_header{
      padding: 10px 10px 0px;
      .shop_icon{
        margin-left:5px;
        color: #999;
      }
      .shop_header_title{
        font-size: 14px;
        line-height:20px;
        color: #999;
      }
    }
  }
}
</style>
