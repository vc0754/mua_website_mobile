<template>
  <div id="app">
    <span style="position:fixed; top:17px; right:60px; z-index:1000;">{{ scrollTop }}</span>
    <header :class="[ 'header', screen_current === 1 ? 'first_screen' : '' ]">
      <div class="inner">
        <img :src="logo[0]" alt="" class="logo" v-if="nav_status">
        <img :src="logo[screen_current === 1 ? 0 : 1]" alt="" class="logo" v-else>
        
        <img :src="nav[3]" alt="" class="nav-switch" v-if="nav_status" @click="nav_switch">
        <img :src="nav[screen_current === 1 ? 1 : 0]" alt="" class="nav-switch" v-else @click="nav_switch">
      </div>
      <nav :class="['nav-wrap', nav_status === 1 ? 'show': '' ]">
        <ul class="nav">
          <li :class="[ nav_current === 0 ? 'active' : '' ]">
            <a href="#" @click="goto(1)">
              <div>
                <span>首</span>
                <span>页</span>
              </div>
              <img src="./assets/icon／右箭头@2x.png" alt="" class="arr">
            </a>
          </li>
          <li :class="[ nav_current === 1 ? 'active' : '' ]">
            <a href="#" @click="goto(2)">
              <div>优秀产品</div>
              <img src="./assets/icon／右箭头@2x.png" alt="" class="arr">
            </a>
          </li>
          <li :class="[ nav_current === 2 ? 'active' : '' ]">
            <a href="#" @click="goto(1)">
              <div>申请代理</div>
              <img src="./assets/icon／右箭头@2x.png" alt="" class="arr">
            </a>
          </li>
        </ul>
      </nav>
    </header>

    <ul :class="['sidepoint', screen_current === 1 ? 'first_screen' : '' ]">
      <li :class="[ screen_current === index ? 'active' : '' ]" v-for="index in 7" :key="index"></li>
    </ul>
    
    <section class="wrap">
      <div class="background-wrap" :style="{ backgroundImage: `url('${require('./assets/背景-移动端官网@2x.png')}')` }"></div>
      <div class="content-layer color-white">
        <img src="./assets/标题@2x.png" alt="" style="width:243px; margin-bottom:50px;">
        <section class="features">
          <ul>
            <li>
              <img src="./assets/icon／创业产品@2x(1).png" alt="" class="icon">
              <div>
                <h4>创业产品免费提供</h4>
                <p>6款产品免费提供，创业不再是梦想</p>
              </div>
            </li>
            <li>
              <img src="./assets/icon／创业产品@2x(2).png" alt="" class="icon">
              <div>
                <h4>产品运营赋能</h4>
                <p>专业导师指导，创业运营无压力</p>
              </div>
            </li>
            <li>
              <img src="./assets/icon／创业产品@2x.png" alt="" class="icon">
              <div>
                <h4>实习 + 转正</h4>
                <p>经验积累，毕业提供实习与转正机会</p>
              </div>
            </li>
          </ul>
        </section>
        <img src="./assets/icon-下一页@2x.png" alt="" class="next-page">
      </div>
    </section>
    
    <!-- 第二屏 -->
    <section ref="ss">
      <nav class="subnav">
        <div class="col" @click="goto2(1)">
          <img src="./assets/主icon 二手闲置2@2x.png" alt="" class="icon">
          <p class="label">二手闲置</p>
        </div>
        <div class="col" @click="goto2(2)">
          <img src="./assets/主icon遇见2@2x.png" alt="" class="icon">
          <p class="label">遇见社交</p>
        </div>
        <div class="col current" @click="goto2(3)">
          <img src="./assets/主icon 体验馆2@2x.png" alt="" class="icon">
          <p class="label">恋爱体验馆</p>
        </div>
        <div class="col" @click="goto2(4)">
          <img src="./assets/主icon校园嗨聊2@2x.png" alt="" class="icon">
          <p class="label">校园嗨聊</p>
        </div>
        <div class="col" @click="goto2(5)">
          <img src="./assets/主icon 代办2@2x.png" alt="" class="icon">
          <p class="label">跑腿代办</p>
        </div>
      </nav>
      
      <div class="cc">
        <div style="margin: 0 -24px;">
          <img src="./assets/遇见社交-01广场@2x.png" alt="">
        </div>
        <div class="info">
          <h3>遇见社交</h3>
          <h5>基于兴趣的大学生社交小程序</h5>
          <p>广场分享日常瞬间； <br/>随意切换广场与本校发布功能，收货更多同学的赞；匿名发布树洞，可缓解学习压力，可吐露心事情绪；设定主页的兴趣标签，大数据匹配你的灵魂校友； 私聊功能，让你与校园同学畅聊；<br/>发布功能可设置自己可见，记录校园私密日记。</p>
        </div>
        <div style="margin: 0 -58px;">
          <img src="./assets/遇见社交-04私聊 + 遇见社交-02发布 + 遇见社交-03我的 蒙版@2x.png" alt="">
        </div>
        
        <img src="./assets/小程序码1@2x.png" alt="" class="qrcode">
        <div class="rqtitle">
          <h4>遇见社交</h4>
          <p>识别小程序码，立即体验</p>
        </div>
      </div>
      
      <div class="cc">
        <div style="margin: 0 -24px;">
          <img src="./assets/恋爱体验馆-01首页@2x.png" alt="">
        </div>
        <div class="info">
          <h3>恋爱体验馆</h3>
          <h5>解救单身狗的大学生恋爱小程序</h5>
          <p>随意切换同城、同校/异校等定位，匹配最优秀的TA 使用「卖室友」功能，有趣好玩，闺蜜兄弟轻松脱单 CP签恋爱小卡片，了解TA，并私聊TA 一周CP恋爱体验活动，助你破冰脱单</p>
        </div>
        <div style="margin: 0 -58px;">
          <img src="./assets/恋爱体验馆-02我喜欢谁 + 恋爱体验馆-04被卖了 + 恋爱体验馆-03cp签 蒙版@2x.png" alt="">
        </div>
        
        <img src="./assets/小程序码1@2x.png" alt="" class="qrcode">
        <div class="rqtitle">
          <h4>遇见社交</h4>
          <p>识别小程序码，立即体验</p>
        </div>
      </div>
      
      <div class="cc">
        <div style="margin: 0 -24px;">
          <img src="./assets/校园嗨聊-01首页@2x.png" alt="">
        </div>
        <div class="info">
          <h3>校园嗨聊</h3>
          <h5>基于语音社交的大学生小程序</h5>
          <p>声控福利，与陌生的TA语音畅聊，喜欢就关注TA 大数据匹配，与相似的你在线畅聊不停<br>互动语音房，兴趣、情感、唠嗑等话题嗨聊不停 PK语音房，来主持一场校园趣味辩论、K歌大赛 体验一把语音直播主持，嗨玩赚零花</p>
        </div>
        <div style="margin: 0 -58px;">
          <img src="./assets/校园嗨聊-02互动房 + 校园嗨聊-04语音匹配 + 校园嗨聊-03语音派对 蒙版@2x.png" alt="">
        </div>
        
        <img src="./assets/小程序码1@2x.png" alt="" class="qrcode">
        <div class="rqtitle">
          <h4>遇见社交</h4>
          <p>识别小程序码，立即体验</p>
        </div>
      </div>
      
      <div class="cc">
        <div style="margin: 0 -24px;">
          <img src="./assets/校园代办-01首页@2x.png" alt="">
        </div>
        <div class="info">
          <h3>校园代办</h3>
          <h5>大学生生活服务小程序</h5>
          <p>悬赏服务费让同学帮忙代取快递<br/>通过悬赏让同学代买、代送物品<br/>自己不想做或不方便的事都可以找同学帮忙<br/>校园免费福利、特惠干货早知道<br/>注册小骑手还可以赚零花钱</p>
        </div>
        <div style="margin: 0 -58px;">
          <img src="./assets/校园代办-02我的 + 校园代办-03发布 + 校园代办-04福利 蒙版@2x.png" alt="">
        </div>
        
        <img src="./assets/小程序码1@2x.png" alt="" class="qrcode">
        <div class="rqtitle">
          <h4>遇见社交</h4>
          <p>识别小程序码，立即体验</p>
        </div>
      </div>
      
      <div class="cc">
        <div style="margin: 0 -24px;">
          <img src="./assets/二手闲置-01首页@2x.png" alt="">
        </div>
        <div class="info">
          <h3>二手闲置</h3>
          <h5>大学生二手闲置小程序</h5>
          <p>同校跨校轻松交易二手闲置<br/>实名认证，放心淘二手<br/>平台担保交易，保障买卖双方物品安全<br/>让你的闲置物品不再闲置</p>
        </div>
        <div style="margin: 0 -58px;">
          <img src="./assets/二手闲置-02担保 + 二手闲置-03商品详情 蒙版@2x.png" alt="">
        </div>
        
        <img src="./assets/小程序码1@2x.png" alt="" class="qrcode">
        <div class="rqtitle">
          <h4>遇见社交</h4>
          <p>识别小程序码，立即体验</p>
        </div>
      </div>
    </section>
    
  </div>
</template>

<script>
import $ from 'jquery';

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      scrolling: false,
      scrollTop: 0,
      screen_current: 1,
      logo: [
        require('./assets/logo0.png'),
        require('./assets/logo1.png')
      ],
      nav: [
        require('./assets/icon-菜单@2x - 副本.png'),
        require('./assets/icon-菜单@2x.png'),
        require('./assets/icon-菜单关闭@2x - 副本.png'),
        require('./assets/icon-菜单关闭@2x.png')
      ],
      nav_current: 0,
      nav_status: 0,
      nav_left: [
        3.5,
        82.5
      ],
      swiper2: null,
      nav2_current: 0,
      nav2_left: [
        23, 23,
        178, 178,
        335, 335,
        485, 485,
        645, 645
      ],
      point: 0
    }
  },
  methods: {
    down(e) {
      console.log(e)
      return
    },
    nav_switch() {
      this.nav_status = this.nav_status === 0 ? 1 : 0
    },
    goto(index) {
      let top = 0
      if (index === 1) {
        top = 0
      } else if (index === 2) {
        top = document.body.clientHeight - 54
      }
      this.scrolling = true
      $('html,body').stop().animate({ scrollTop: `${top}px` }, 360, () => {
        this.screen_current = index
        this.scrolling = false
      })
      this.nav_status = 0
    },
    goto2(index) {
      console.log(index)
    },
    prev() {
      if (this.nav2_current === 0) return
      this.swiper2.slideTo(this.nav2_current - 1)
    },
    next() {
      if (this.nav2_current === 9) return
      this.swiper2.slideTo(this.nav2_current + 1)
    },
    handleScroll() {
      this.$nextTick(() => {
        this.top = window.pageYOffset
      })
      // console.log()
      // this.top = 
      // if (this.scrolling) return
      // this.scrolling = true
      // if (e.deltaY > 0) {
      //   if (this.screen_current === 1) this.screen_current = 2
      //   $('html,body').animate({ scrollTop: `${document.body.clientHeight}px` }, 500, () => {
      //     this.scrolling = false
      //   })
      // } else {
      //   if (this.screen_current === 2) this.screen_current = 1
      //   $('html,body').animate({ scrollTop: `0px` }, 500, () => {
      //     this.scrolling = false
      //   })
      // }

      // return

      // // console.log(e)
      // if (e.deltaY > 0) {
      //   this.screen_current++
      //   // this.$refs.ss.scrollIntoView({ behavior: "smooth" });
      //   // this.$nextTick(() => {
      //   //   this.$refs.ss.scrollTo(0, 200, true)
      //   // })
      //   // document.documentElement.scrollTop = 500;
      //   // this.$nextTick(() => {
      //   //   console.log(this.$refs)
      //   //   this.$refs.ss.scrollIntoView({ behavior: "smooth" });
      //   // })
      //   // this.swiper.slideTo(1)
      // } else {
      //   this.screen_current = 1
      //   // this.swiper.slideTo(0)
      // }
      
      // this.$nextTick(() => {
      //   setTimeout(() => {
      //     let targetbox= document.getElementById('targetbox');
      //     this.target= targetbox.offsetTop;        
      //   })
      // })
      // document.body.scrollTop = 300;
      // document.getElementById("app").scrollIntoView();
      
      // document.documentElement.scrollTop = 500;
      // console.log(this.$refs.result.scrollIntoView)
      // this.$refs.result.scrollIntoView({ behavior: "smooth" });
    }
  },
  mounted(){
    // try {
    //   window.addEventListener("mousewheel", this.handleScroll) || window.addEventListener("DOMMouseScroll", this.handleScroll);
    // } catch(e) {
    //   window.attachEvent("mousewheel", this.handleScroll);
    // }

    // console.log(document.body.scrollHeight);
    // var a = document.body.scrollHeight;

    window.addEventListener("scroll", () => {
      this.scrollTop = document.documentElement.scrollTop || window.pageYOffset || document.body.scrollTop;
      
      if (!this.scrolling) {
        let height = document.body.clientHeight - 54
        if (this.scrollTop > 0 && this.screen_current === 1) {
          this.scrolling = true
          $('html,body').stop().animate({ scrollTop: `${height}px` }, 360, () => {
            this.scrolling = false
            this.screen_current = 2
          })
        } else if (this.scrollTop < height && this.screen_current === 2) {
          this.scrolling = true
          $('html,body').stop().animate({ scrollTop: `0px` }, 360, () => {
            this.screen_current = 1
            this.scrolling = false
          })
        }
      }
      // console.log(scrollTop);
      // if (scrollTop > (a/2)){
      //   console.log('xxxxxxxxxxxxxxxxxxx');
      // }
    });

  }
}
</script>

<style lang="less">
html, body, #app { height: 100%;}
img { max-width: 100%;}
#app { background-color: #fff;}
.color-white { color: #fff;}

.header {
  background-color: #fff;
  position: fixed; top: 0; left: 0; right: 0; z-index: 100;
  padding: 16px 16px 0 16px;
  .inner {
    padding-bottom: 16px;
    border-bottom: solid 0.5px rgba(255, 255, 255, .15);
    display: flex; justify-content: space-between; align-items: center;
  }
  .logo { width: 93.33px; position: relative; z-index: 1;}
  .nav-switch { width: 20px; height: 20px; position: relative; z-index: 1;}
  .nav-wrap {
    font-size: 17px; width: 100%; height: 100%;
    display: none; justify-content: center; align-items: center;
    position: fixed; top: 0; left: 0;

    ul {
      list-style: none;
      li {
        padding: 0; margin-bottom: 50px;
        a {
          color: #fff;
          display: flex; justify-content: space-between; align-items: center;
        }
        div { min-width: 68px; display: flex; justify-content: space-between;}
        .arr { width: 13px; height: 13px; margin-left: 12px;}
      }
    }
    &.show { display: flex; }
    &::before {
      background-color: rgba(0,0,0,1);
      content: ''; display: block; width: 100%; height: 100%;
      position: absolute; top: 0; left: 0; z-index: -1;
    }
  }

  &.first_screen {
    background-color: transparent;
  }
}

.sidepoint {
  position: fixed; right: 10px; top: 50%; z-index: 90;
  transform: translate3d(0, -50%, 0);
  li {
    list-style: none;
    background-color: #F0F0F0;
    width: 6px; height: 6px; border-radius: 50%;
    margin-bottom: 12px;
    &.active {
      background-color: #24D9BA;
    }
  }
  &.first_screen {
    li {
      background-color: #fff;
      &.active {
        background-color: #24D9BA;
      }
    }
  }
}

.subnav {
  background-color: #eee;
  background-color: #fff;
  width: 100%;
  position: sticky; top: 53px;
  padding: 12px 16px; margin-bottom: 10px;
  display: flex; justify-content: space-between; align-items: center;
  .col {
    display: flex; flex-direction: column; align-items: center;
    .icon { width: 20px; height: 20px; margin-bottom: 5px;}
    .label { color: #808080; font-size: 10px;}
    &.current {
      .icon { width: 32px; height: 32px; margin-bottom: 5px;}
      .label { color: #000; font-size: 15px;}
    }
  }
}

.wrap {
  height: 100%;
  position: relative; z-index: 0;
}
.background-wrap {
  position: absolute; top: 0; right: 0; bottom: 54px; left: 0; z-index: 0;
  background-size: cover; background-position: center bottom; background-repeat: no-repeat;
  &::after {
    background-color: rgba(0,0,0,0.7);
    position: absolute; top: 0; right: 0; bottom: 0; left: 0; z-index: 0;
    content: ''; display: block; width: 100%; height: 100%;
  }
}
.content-layer {
  position: absolute; top: 0; right: 0; bottom: 0; left: 0; z-index: 1;
  display: flex; flex-direction: column; justify-content: center; align-items: center;
}
.features {
  margin-bottom: 65px;
  ul {
    list-style: none;
    li {
      padding: 0; margin-bottom: 28px;
      display: flex; align-items: center;
      .icon { width: 36px; margin-right: 14px;}
      h4 { font-size: 15px;}
      p { font-size: 10px;}
    }
  }
}
.next-page {
  width: 20px; height: 29px;
  position: absolute; left: 50%; bottom: 74px;
  transform: translate3d(-50%, 0, 0);
}
.cc {
  width: 100%; overflow: hidden;
  padding: 16px; padding-bottom: 80px;
  .info {
    padding: 20px 20px 30px;
    font-size: 13px;
    color: #7D7D7E;
    h3 {
      font-size: 20px; font-weight: 500;
      color: #333333;
    }
    h5 {
      font-size: 15px; font-weight: 400;
      color: #333333;
      margin: 10px 0;
    }
    p { line-height: 24px;}
  }
}

.qrcode { width: 80px; height: 80px; margin: 28px auto 16px; display: block;}
.rqtitle { color: #333; text-align: center;
  h4 { font-size: 20px; font-weight: 500; margin-bottom: 10px;}
  p { font-size: 15px;}
}

/*
.fs-13 { font-size: 13px;}
.fs-15 { font-size: 15px;}
.fs-20 { font-size: 20px;}
.fs-70 { font-size: 70px;}
.fs-72 { font-size: 72px;}

.flex { display: flex;}
.flex-x-between { justify-content: space-between;}
.flex-x-center { justify-content: center;}
.flex-y-center { align-items: center;}
.flex-column { flex-direction: column;}

.swiper-container {
  width: 100%; height: 100%;
  .swiper-slide {
    position: relative;
    .bg {
      width: 150%; height: 100%;
      position: absolute; top: 0; left: 0;
      background-position: center bottom;
      background-repeat: repeat-x;
      animation: slide 3s ease-in-out infinite alternate;
    }
  }
}

@keyframes slide {
  0% {
    transform: translateX(-25%);
  }
  100% {
    // transform: translateX(25%);
  }
}

.header {
  position: fixed; top: 20px;
  width: 100%;
  z-index: 100;
  .logo { position: relative;}
  a {
    color: #fff; text-decoration: none;
    &:hover { color: #fff; text-decoration: none;}
  }
  .nav-wrap {
    position: relative;
    .nav {
      color: #fff;
      font-size: 14px;
      display: flex;
      li {
        padding: 4px 0; margin-left: 36px;
        position: relative;
        &:first-child { margin-left: 0;}
      }
    }
    .nav-link {
      display: block; content: '';
      width: 20px; height: 3px; padding: 0;
      background: #24D9BA;
      border-radius: 2px;
      position: absolute; bottom: 0;
    }
  }
  
  &.secondary {
    a { color: #A3A3A3; }
    li.active {
      a { color: #000;}
    }
  }
}

.hero {
  background-color: #eee;
  height: 54%;
  position: relative;
  .background {
    background-position: center center;
    background-repeat: no-repeat;
    background-size: cover;
    width: 100%; height: 100%;
    position: relative;
    &::after {
      display: block; content: ''; width: 100%; height: 100%;
      background-color: rgba(0, 0, 0, 0.6);
    }
  }
  .content-layer {
    position: absolute; top: 0; left: 0;
    width: 100%; height: 100%;
    color: #fff;
    display: flex; justify-content: center; align-items: center;
    padding-top: 115px;
  }
}



.subnav {
  color: #808080;
  border-bottom: solid 1px rgba(0, 0, 0, 0.1);
  .container { position: relative;}
  .nav-link {
    display: block; content: '';
    width: 107px; height: 3px; padding: 0;
    background: #24D9BA;
    border-radius: 2px;
    position: absolute; bottom: 0;
  }
}

@media (min-height: 800px) {
  .subnav { margin-bottom: 20px; }
}
@media (min-height: 820px) {
  .subnav { margin-bottom: 40px; }
}
@media (min-height: 850px) {
  .subnav { margin-bottom: 60px; }
}

.swiper-container-2 {
  .container {
    width: 774px; height: 380px; margin: 0 auto; position: relative;
  }
  .row { height: 100%;}
  h3 { color: #333; font-size: 20px; margin-bottom: 12px;}
  h5 { color: #333; font-size: 15px; margin-bottom: 16px;}
  p { color: #7D7D7E; font-size: 13px; line-height: 20px;}
}

.arrs {
  width: 920px;
  position:absolute; top:50%; left:50%; z-index:100;
  transform: translate3d(-50%, 0, 0);
  .arr-left { position: absolute; left: 0;}
  .arr-right { position: absolute; right: 0;}
}

.point {
  position: absolute; bottom: 67px; left: 50%; z-index: 100;
  transform: translate3d(-50%, 0, 0);
  display: flex;
  span {
    display: block; margin: 0 6px;
    background: rgba(0, 0, 0, 0.3);
    width: 10px; height: 10px; border-radius: 5px;
    &.active { background: #fff; width: 16px;}
  }
}
*/
</style>
