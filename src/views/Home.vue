<template>
  <div class="container">
    <div class="logo-container" v-if="showLogo">
      <div class="logo-section">
        <img src="@/assets/apple.png" alt="" class="logo-image_apple">
        <div class="logo-ling">
          <div class="logo-ling-show"></div>
        </div>
      </div>
    </div>
    <div class="OnThePage-container" v-if="OnThePage">
      <div class="OnThePage-section">
         <div class="user-info">
           <div class="user-info_image" @click="passwordEditShow">
            <img src="@/assets/portrait-04.png" alt="">
           </div>
           <p class="user-name">xing Xing</p>
          <div class="boot-input" v-show="passwordEditShowling">
            <img src="@/assets/log-arrow-left-07.png" @click="passwordEditShowhide" class="boot-input_logo" />
            <input class="boot-input_content" placeholder="Enter whatever you want" type="text" @keyup.enter="boot">
          </div>
          <img class="load" src="@/assets/load.gif"  v-show="load" alt="">
         </div>
         <div class="operation-container">
           <div class="operation-section">
             <img src="@/assets/Sleep-04.png" @click="showOverspread" alt="" class="operation-sleep">
             <img src="@/assets/shut-06.png" @click="close" alt="" class="operation-shut_down">
             <img src="@/assets/restart-05.png" alt="" @click="restart" class="operation-restart">
           </div>
         </div>
      </div>
    </div>
    <div v-if="overspread"  @click="showOverspread" class="overspread-container"></div>
    <div class="page-container">
      <div class="page-section">
        <div class="page-header">
          <div class="header-left">
            <img src="@/assets/apple.png" alt="" class="header-logo_apple">
            <div class="heaedr-hovwe_button">
              <p class="heaedr-hovwe_button-title">我</p>
              <div class="heaedr-hovwe_button-select_list">
                <p class="heaedr-hovwe_button-select_item" @click="addUserinfo(0)">关于我</p>
              </div>
            </div>
            <div class="heaedr-hovwe_button">
              <p class="heaedr-hovwe_button-title heaedr-hovwe_button_show">文件</p>
              <!-- <div class="heaedr-hovwe_button-select_list">
                <p class="heaedr-hovwe_button-select_item">App设计稿原型</p>
                <p class="heaedr-hovwe_button-select_item">观看App设计稿原型</p>
                <p class="heaedr-hovwe_button-select_item">案例研究</p>
                <p class="heaedr-hovwe_button-select_item">界面讨论</p>
              </div> -->
            </div>
            <div class="heaedr-hovwe_button heaedr-hovwe_button_show">
              <p class="heaedr-hovwe_button-title  heaedr-hovwe_button-title-show">看法</p>
              <!-- <div class="heaedr-hovwe_button-select_list">
                <p class="heaedr-hovwe_button-select_item"></p>
              </div> -->
            </div>
             <div class="heaedr-hovwe_button">
              <p class="heaedr-hovwe_button-title">技术支持</p>
              <div class="heaedr-hovwe_button-select_list">
                <p class="heaedr-hovwe_button-select_item">
                  <a class="target" href="https://cn.vuejs.org/" target="_blank">vue</a>
                </p>
                 <p class="heaedr-hovwe_button-select_item">
                  <a class="target" href="https://developers.weixin.qq.com/miniprogram/dev/framework/" target="_blank">微信小程序</a>
                </p>
                <p class="heaedr-hovwe_button-select_item">
                  <a class="target" href="https://www.qiniu.com/" target="_blank">七牛云</a>
                </p>
                <p class="heaedr-hovwe_button-select_item">
                  <a class="target" href="http://element.eleme.io/#/zh-CN" target="_blank">element</a>
                </p>
                <p class="heaedr-hovwe_button-select_item">
                  <a class="target" href="https://lanhuapp.com/?home" target="_blank">蓝湖</a>
                </p>
                <p class="heaedr-hovwe_button-select_item">
                  <a class="target" href="https://www.kancloud.cn/liuwave/quill/1409423" target="_blank">quill</a>
                </p>
                <p class="heaedr-hovwe_button-select_item">
                  <a class="target" href="https://www.expressjs.com.cn/" target="_blank">expressjs</a>
                </p>
                <p class="heaedr-hovwe_button-select_item">
                  <a class="target" href="https://knexjs.org/" target="_blank">knex</a>
                </p>
              </div>
            </div>
            <div class="heaedr-hovwe_button">
              <p class="heaedr-hovwe_button-title" >关于我</p>
              <div class="heaedr-hovwe_button-select_list">
                <p class="heaedr-hovwe_button-select_item"  @click="addUserinfo(1)">陈剑涛</p>
                <p class="heaedr-hovwe_button-select_item"  @click="addUserinfo(2)">联系方式</p>
                <p class="heaedr-hovwe_button-select_item"  @click="addUserinfo(3)">教育经历</p>
                <p class="heaedr-hovwe_button-select_item"  @click="addUserinfo(4)">所在地</p>
                <p class="heaedr-hovwe_button-select_item"  @click="addUserinfo(5)">前端工程师</p>
              </div>
            </div>
          </div>
          <div class="header-right">
            <p class="date-title">{{week}}</p>
            <p class="time-title">{{newTime}}</p>
            <img src="@/assets/Drawer.png" @click="editFlexible" alt="" class="Drawer-show">
          </div>
        </div>
        <div class="page-content">
          <Drawer :flexible="flexible"/>
          <VueDragResize :isActive="false" :isResizable="true" :x="100" :y="50"  :w="1600" :h="800" :z="srcZ[index]" @clicked="addZ(index)" :parentLimitation="true" v-for="( item, index ) in windowContainer" :key="item">
            <div class="window-container" >
            <div class="window-section">
              <div class="window-header">
                <div class="handle-section">
                  <div class="del" @click="delWindowContainer(index)"></div>
                  <!-- <div class="flex"></div> -->
                </div>
              </div>
              <iframe class="window-body" :src="item"></iframe>
            </div>
          </div>
          </VueDragResize>
          <VueDragResize :isActive="false" :isResizable="true" :x="300" :y="200" :w="432" :h="200" :z="item.index" @clicked="addReferralContentZ(index)" :parentLimitation="true" v-for="( item, index ) in referralContentArr" :key="item.content">
            <referral :content="item" @update:quitReferralContent="quitReferralContent(index)"></referral>
          </VueDragResize>
        </div>
        <div class="page-footer">
          <div class="page-footer_container">
            <div class="app-img-section">
              <img src="@/assets/aitschool.png" alt="QQ音乐" @click="addSrc(0)" class="app-img">
              <p class="app-img_desc">aitschool</p>
            </div>
            <div class="app-img-section">
              <img src="@/assets/dx.svg" alt="斗西" @click="addSrc(1)" class="app-img">
              <p class="app-img_desc">斗西</p>
            </div>
            <div class="app-img-section">
              <img src="@/assets/dx.svg" alt="斗西计划" @click="addSrc(2)" class="app-img">
              <p class="app-img_desc">斗西计划</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Drawer from '@/components/Drawer.vue'
import referral from '@/components/referral.vue'

import VueDragResize from 'vue-drag-resize'
export default {
  name: 'Home',
  data () {
    return {
      Zindex: 0,
      referralContentArr: [{
        title: '你好',
        desc: '这是我的个人简介页面',
        index: 1

      }],
      srcZ: [0, 0, 0],
      src: ['https://www.aitschool.com/', 'https://www.daylab.cn/works', 'https://www.home-plan.cn/'],
      windowContainer: [],
      flexible: false,
      week: null,
      newTime: null,
      load: false,
      OnThePage: true,
      passwordEditShowling: true,
      showLogo: true,
      overspread: false
    }
  },
  components: {
    referral,
    Drawer,
    VueDragResize
  },
  beforeCreate () {
  },
  beforeMount () {
    this.showLogoTime()
  },
  created () {
    this.getTime()
  },
  beforeDestroy () {
    if (this.timer) {
      clearInterval(this.timer) // 在Vue实例销毁前，清除我们的定时器
    }
  },
  methods: {
    addUserinfo (index) {
      const length = this.referralContentArr.length
      switch (index) {
        case 0 :
          this.referralContentArr[0] = {
            title: '你好',
            desc: '这是我自己展示自己作品的平台,使用Vue CLI框架搭建',
            index: length
          }
          break
        case 1 :
          this.referralContentArr[0] = {
            title: '你好',
            desc: '我叫陈剑涛，',
            index: length
          }
          break
        case 2 :
          this.referralContentArr[0] = {
            title: '你好',
            desc: '我的手机号码为185********',
            index: length
          }
          break
        case 3 :
          this.referralContentArr[0] = {
            title: '你好',
            desc: '我目前在广东生态工程学院就读',
            index: length
          }
          break
        case 4 :
          this.referralContentArr[0] = {
            title: '你好',
            desc: '我目前在广州增城区',
            index: length
          }
          break
        case 5 :
          this.referralContentArr[0] = {
            title: '你好',
            desc: '我是一位前端工程师',
            index: length
          }
          break
      }
    },
    quitReferralContent (index) {
      this.referralContentArr.splice(index, 1)
    },
    addReferralContentZ (index) {
      this.referralContentArr.forEach(item => {
        item.index = 0
      })
      this.referralContentArr[index].index += this.Zindex += 2
    },
    addZ (index) {
      this.srcZ = [0, 0, 0]
      this.srcZ[index] = this.Zindex += 2
    },
    delWindowContainer (index) {
      this.windowContainer.splice(index, 1)
    },
    addSrc (index) {
      if (this.windowContainer.indexOf(this.src[index])) {
        this.windowContainer.unshift(this.src[index])
        this.srcZ[0] = this.Zindex += 2
      }
    },
    editFlexible () {
      this.flexible = !this.flexible
    },
    getTime () {
      this.timer = setInterval(() => {
        const date = new Date()
        const hour = date.getHours()
        const minute = date.getMinutes()
        const second = date.getSeconds()
        const formatNumber = n => {
          n = n.toString()
          return n[1] ? n : '0' + n
        }
        this.newTime = [hour, minute, second].map(formatNumber).join(':') // 修改数据date
        var a = ['日', '一', '二', '三', '四', '五', '六']
        var week = date.getDay()
        this.week = '周' + a[week]
      }, 1000)
    },
    boot () {
      this.load = true
      this.passwordEditShowling = false
      setTimeout(() => { this.OnThePage = false }, 2000)
    },
    passwordEditShowhide () {
      this.passwordEditShowling = false
    },
    passwordEditShow () {
      this.passwordEditShowling = true
    },
    restart () {
      location.reload()
    },
    close () {
      window.opener = null
      window.open('', '_self')
      window.close()
    },
    showOverspread () {
      this.overspread = !this.overspread
    },
    showLogoTime () {
      setTimeout(() => { this.showLogo = false }, 3200)
    }
  }
}
</script>
<style lang="less" scoped>
.container{
  height: 100vh;
  width: 100%;
  .logo-container{
    position: fixed;
    top:0;
    left: 0;
    z-index: 14;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 1);
    display: flex;
    align-items: center;
    flex-direction: column;
    padding-top: 240px;
    .logo-section{

      .logo-image_apple{
        width: 300px;
        height: 180px;
      }
      .logo-ling{
        width: 210px;
        height: 8px;
        border: solid 1px #fff;
        margin: 30px auto;
        border-radius: 20px;
        .logo-ling-show{
          height: 100%;
          width: 100%;
          background-color: #fff;
          animation: showLing 3s linear 1;
          animation-fill-mode:forwards
        }
      }
    }
  }
  .OnThePage-container{
    height: 100%;
    width: 100%;
    position: fixed;
    left: 0;
    top: 0;
    z-index: 12;
    background-color: rgba(0, 0, 0, 0.9);
    .OnThePage-section{
      height: 100%;
      width: 100%;
      display: flex;
      align-items: center;
      flex-direction: column;
      padding-top: 130px;
      justify-content: space-around;
      .user-info{
        display: flex;
        align-items: center;
        flex-direction: column;
        // justify-content: space-around;
        height: 194px;
        .user-info_image{
          width: 82px;
          height: 82px;
          background-color: #fff;
          border-radius: 50%;
          display: flex;
          justify-content: center;
          align-items: center;
          img{
            width: 48px;
            height: 70px;
          }
        }
        .user-name{
          font-size: 16px;
          margin: 24px 0;
          color: #fff;
        }
        .boot-input{
          display: flex;
          align-items: center;
          justify-content: center;
          padding-right: 60px;
          .boot-input_logo{
            border-radius: 50%;
            width: 32px;
            height: 32px;
            margin: 0 20px
          }
          .boot-input_content{
            height: 42px;
            width: 200px;
            border-radius: 5px;
            background-color: rgba(250, 250, 250, 0.2);
            border: none;
            outline: none;
            padding: 10px 10px;
          }
        }
        .load{
          width: 70px;
          height: 60px;
        }
      }
      .operation-container{
        .operation-section{
          display: flex;
          width: 348px;
          justify-content: space-between;
          align-items: center;
          img{
            height: 54px;
          }
        }
      }
    }
  }
  .overspread-container{
    height: 100%;
    width: 100%;
    position: fixed;
    left: 0;
    top: 0;
    z-index: 16;
    background-color: rgba(0, 0, 0, 0.1);
    animation: overspread 2s linear 1;
    animation-fill-mode:forwards
  }
  .page-container{
    height: 100%;
    width: 100%;
    overflow:hidden;
    background-image: url('./../assets/page.jpeg');
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    .page-section{
      height: 100%;
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      .page-header{
        display: flex;
        justify-content: space-between;
        flex-direction: row;
        background-color: #000;
        color: #fff;
        .header-left{
          display: flex;
          align-items: center;
          .header-logo_apple{
            height: 30px;
          }
          .heaedr-hovwe_button{
            position: relative;
            margin: 0 10px;
            .heaedr-hovwe_button-title{
              font-size: 14px;
              line-height: 30px;
              padding: 0 10px;
              cursor:pointer;
              &:hover{
                background-color: #0063ec;
              }
            }
            .heaedr-hovwe_button-title-show{
                &:hover{
                  background-color: inherit;
                }
              }
            .heaedr-hovwe_button-select_list{
              z-index: 9;
              display: none;
              position: absolute;
              white-space: nowrap;
              top: 100%;
              padding: 10px 0;
              background-color: #333;
              border-radius: 0 0 5px 5px;
              .heaedr-hovwe_button-select_item{
                cursor:pointer;
                font-size: 14px;
                padding: 0 18px;
                margin: 10px 0;
                &:hover{
                  background-color: #0063ec;
                }
                a{
                  text-decoration: none;
                  color: #fff;
                }
              }
            }
            &:hover{
               .heaedr-hovwe_button-select_list{
                 display: inline-block;
               }
            }
          }
          .heaedr-hovwe_button_show{
            color: #999;
          }
        }
        .header-right{
          display: flex;
          align-items: center;
          .date-title, .time-title, .Drawer-show{
            margin: 0 10px;
            font-size: 14px;
            cursor:default;
          }
          .Drawer-show{
            height: 15px;
          }
          .time-title{
            width: 60px;
          }
        }
      }
      .page-content{
        flex: 1;
        position: relative;

        .window-container,.window-section{
          position: absolute;
          top: 0;
          width: 100%;
          height: 100%;
          margin: 0 auto;
          background-color: #fff;
          .window-header{
            background-color: #f5f5f5;
            border: 5px 0 5px 0;
            height: 25px;
            .handle-section{
              display: flex;
              .del{
                width: 15px;
                height: 15px;
                border-radius: 50%;
                background-color: #999;
                margin: 5px;
              }
              .flex{
                width: 15px;
                height: 15px;
                border-radius: 50%;
                background-color:#999;
                margin: 5px
              }
              &:hover {
                .del {
                  background-image: url('./../assets/x.png');
                  background-size: cover;
                }
                .flex {
                  background-image: url('./../assets/magnify.png');
                  background-size: cover;
                }
              }
            }
          }
          .window-body{
            height: calc(100% - 25px);
            width: 100%;

          }
        }
      }
    }
  }
  .page-footer{
    text-align: center;
    padding-bottom: 5px;
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    .page-footer_container{
      display: inline-block;
      padding: 10px;
      background: #0f0f0f72;
      border-radius: 5px;
      .app-img-section{
        display: inline-block;
        position: relative;
        .app-img{
          width: 32px;
          height: 33px;
          margin: 0 10px;
          border-radius: 8px;
          background-color: #fff;
        }
        .app-img_desc{
          display: none;
          position: absolute;
          color: #333;
          padding: 0 6px;
          font-size: 15px;
          top: -100%;
          left: 50%;
          transform: translateX(-50%);
          width: auto;
          white-space: nowrap;
          background-color: #fff;
          border-radius: 3px;
          &:after{
            position: absolute;
            top: 100%;
            left: 50%;
            transform: translateX(-50%);
            content: '';
            display: inline-block;
            width: 0;
            height: 0;
            border-top: 5px solid #fff;
            border-right: 5px solid transparent;
            border-bottom: 5px solid transparent;
            border-left: 5px solid transparent;
          }
        }
        &:hover{
          .app-img_desc{
            display: inline-block;
          }
        }
      }
    }
  }
}
/deep/.vdr-stick,.vdr-stick-tl{
  display: none;
}
/deep/.vdr::before{
  outline: none !important;
}
@keyframes showLing {

  0%{
    width: 0%;
  }
  100%{
    width: 100%;
  }
}
@keyframes overspread {

  0%{
    background-color: rgba(0, 0, 0, 0.1);

  }
  100%{
    background-color: rgba(0, 0, 0, 1);

  }
}
</style>
