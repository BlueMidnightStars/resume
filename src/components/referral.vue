<template>
  <div class="referral-container">
    <div class="header"></div>
    <div class="content">
      <div class="content-container">
        <!-- <img src="" alt="" class="content-left"> -->
        <div class="content-text">
          <p class="title">{{content.title}}</p>
          <p class="desc">{{content.desc}}</p>
        </div>
      </div>
      <button class="quit" @click="quitReferralContent">好的</button>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    referral: Boolean,
    content: Object
  },
  methods: {
    quitReferralContent () {
      this.$emit('update:quitReferralContent')
    }
  }
}
</script>
<style lang="less" scoped>
.referral-container{
  width: 432px;
  min-height: 200px;
  // position: absolute;
  // left: 300px;
  // top: 300px;
  background: #f0f0f0;
  border-radius: 4px;
  box-shadow: 1px 1px 22px rgb(15 15 15 / 50%);
  display: flex;
  flex-direction:column;
  .header{
    height: 24px;
    border-radius: 5px 5px 0 0;
    background-color: rgb(217 216 217);
  }
  .content{
    display: flex;
    flex-direction:column;
    flex: 1;
    .content-text{
      flex: 1;
      padding: 20px;
      min-height: 130px;
      .title{
        font-size: 16px;
        color: #333;
        font-weight: 600;
      }
      .desc{
        font-size: 14px;
        color: #999;
        font-weight: 400;
      }
    }
    .quit{
      margin: 10px auto;
      height: 30px;
      padding: 0 20px;
      border: none;
      background: linear-gradient( #4b96f4, #2d63d6);
      border-radius: 3px;
      color: #fff;
      font-size: 12px;
    }
  }
}
</style>
