<template>
  <div v-show="show" :class="['Drawer-container',{flexible: flexible},'show'] ">
    <div class="section">
      <div class="user-info">
        <div class="user-info-link link">
          个人信息
        </div>
        <div class="user-container">
          <p class="user-name">陈剑涛</p>
          <p class="user-desc">前端工程师</p>
          <p class="user-site">驻广州</p>
        </div>
      </div>
      <div class="user-education">
        <p class="user-education-link link">
          教育信息
        </p>
        <div class="education-class-container">
          <div class="education-class_link">
            <p class="class-name">市场营销</p>
            <p class="class-date">2020.10</p>
          </div>
          <p class="education-name">大专</p>
          <p class="education-school">广东生态工程职业学院</p>
        </div>
      </div>
      <div class="skill-container">
        <p class="skill-link link">
            技能
        </p>
        <div class="skill-section">
          <div class="skill-list">
            <p class="skill-item">
              html
            </p>
            <p class="skill-item">
              css
            </p>
            <p class="skill-item">
              less
            </p>
            <p class="skill-item">
              javascript
            </p>
            <p class="skill-item">
              jQuery.js
            </p>
             <p class="skill-item">
              Vue.js
            </p>
            <p class="skill-item">
              node.js
            </p>
             <p class="skill-item">
              Express
            </p>
            <p class="skill-item">
              koa
            </p>
            <p class="skill-item">
              egg
            </p>
            <p class="skill-item">
              git
            </p>
            <p class="skill-item">
              微信小程序
            </p>
            <p class="skill-item">
              Element
            </p>
          </div>
        </div>
      </div>
      <div class="capacity-container">
        <div class="capacity-section">
          <p class="capacity-link link">
            个人能力
          </p>
          <div class="capacity-list">
            <p class="capacity-item">
              勤劳
            </p>
            <p class="capacity-item">
              解决能力
            </p>
            <p class="capacity-item">
              设计思维
            </p>
            <p class="capacity-item">
              有创造力
            </p>
            <p class="capacity-item">
              快速精益
            </p>
            <p class="capacity-item">
              优秀
            </p>
            <p class="capacity-item">
              勤奋
            </p>
            <p class="capacity-item">
              坚强
            </p>
            <p class="capacity-item">
              吃苦耐劳
            </p>
          </div>
        </div>
      </div>
      <div class="work-container">
        <div class="work-section">
          <p class="work-link link">
            工作经历
          </p>
          <div class="work-list">
            <div class="work-item">
               <p class="work-desc">扎克斯(广州)科技有限公司</p>
              <p class="work-item_title">前端工程师</p>
              <p class="work-date">2018年-至今</p>
              <p class="work-item_text">
                1.教学业务部（ EDU ）相关研发落地，包含：前台、后台、微信小程序。<br/>
                2.企业业务部（ 外包 ）相关项目交付，包含：极客学院、是光、留音社等。<br/>
                3.帮助新同事熟悉业务，结合业务和数据场景输出合理的前后台管理方案。<br/>
                4.旧项目的日常迭代、基础项目上线测试。
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      show: false
    }
  },
  props: {
    flexible: Boolean
  },
  watch: {
    flexible: function (value) {
      if (value) this.show = true
    }
  }
}
</script>
<style lang="less" scoped>
.Drawer-container{
  width: 352px;
  height: 100%;
  position: absolute;
  right: 0;
  top: 0;
  overflow: auto;
  background: rgb(63 65 69 / 1);
  color: rgba(255,255,255,0.7);
  animation: positionR 0.8s linear 1;
  transform: translateX(100%);
  // animation-fill-mode:forwards
  &::-webkit-scrollbar {
    display: none;
  }
  .link{
    padding: 0 36px;
    font-size: 12px;
    line-height: 32px;
    background-color: #0f0f0f;;
  }
  .user-info{
    .user-info-link{
      font-size: 15px;
    }
    .user-container{
      padding: 10px 36px;
      .user-name{
        font-size: 21px;
        line-height: 28px;
      }
      .user-desc,.user-site{
        font-size: 12px;
        line-height: 20px;
      }
    }
  }
  .user-education{
    .education-class-container{
      padding: 10px 36px;
      font-size: 12px;
      border-bottom: 3px solid rgba(255,255,255,0.1);
      .education-class_link{
        display: flex;
        justify-content: space-between;
        align-items: center;
        .class-date{
          font-weight: 300;
        }
      }
      .education-name{
        opacity: 0.5;
        line-height: 18px;
      }
      .education-school{
        line-height: 30px;
      }
    }
  }
  .skill-container{
    .skill-section{
      padding: 10px 36px;
      font-size: 12px;
      .skill-list{
        display: flex;
        flex-wrap: wrap;
        .skill-item{
          width: 50%;
          line-height: 22px;
        }
      }
    }
  }
  .capacity-container{
    .capacity-section{
      .capacity-list{
        padding: 10px 36px;
        font-size: 12px;
        .capacity-item{
          line-height: 22px;
        }
      }
    }
  }
  .work-container{
    .work-section{
      .work-list{
        padding: 10px 36px;
        font-size: 12px;
        .work-item_title{
          font-weight: 600;
          line-height: 30px;
        }
        .work-date{
          font-weight: 400px;
          line-height: 20px;
        }
        .work-desc,.work-item_text{
          opacity: 0.5;

        }
      }
    }
  }
}
.flexible{
animation: flexible 0.8s linear 1;
transform: translateX(0%);
}
@keyframes flexible {

  0%{
    transform: translateX(100%);
  }
  100%{
    transform: translateX(2%);
  }
}
@keyframes  positionR{

  0%{
    transform: translateX(0%);
  }
  100%{
    transform: translateX(100%);
  }
}
</style>
