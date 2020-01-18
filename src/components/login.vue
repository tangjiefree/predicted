<template>
  <div class="login" v-show="showLogin">
    <span class="close" @click="closeToast()"></span>
    <div class="titleBlock">
      <van-tabs v-model="active">
        <van-tab title="用户登陆" class="signin">
          <input placeholder="请输入手机号" type="text">
          <input placeholder="请输入密码" type="password">
          <button>登陆</button>
          <p>忘记密码?</p>
        </van-tab>
        <van-tab title="新用户注册" class="regist">
          <div class="common">
            <input placeholder="请输入手机号" type="text">
          </div>
          <div class="common">
            <input placeholder="请输入密码" type="password">
          </div>
          <div class="yz common">
            <input type="text">
            <img :src="ewm" alt="" @click="refeshEWM()">
          </div>
          <div class="yz common">
            <input type="text">
            <span @click="getMessage()">获取验证码</span>
          </div>
          <button>下一步</button>
        </van-tab>
      </van-tabs>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showLogin: false,
      active: 1,
      ewm: ''
    }
  },
  mounted() {
    this.getEWM()
  },
  methods: {
    closeToast() {
      this.showLogin = false;
    },
    getEWM() {
      this.$axios.get('/api/party/nologin/v2/user/verifyImage?width=170&height=56')
      .then(res => {
        console.log(res)
        this.ewm = res.data.verifyImage;
      })
    },
    refeshEWM() {
      this.getEWM()
    },
    getMessage() {

    }
  }
}
</script>

<style lang="less" scoped>
.login {
  padding-top: 1.15rem;
  width:6.3rem;
  height: 6.61rem;
  margin: 0 auto;
  background: url(../assets/login.png) no-repeat;
  background-size: contain;
  position: relative;
  .close {
    width: 0.4rem;
    height: 0.4rem;
    background: url(../assets/close.png) no-repeat;
    background-size: contain;
    position: absolute;
    right: .4rem;
    top: .23rem;
  }
  .titleBlock {
    .signin {
      input {
        width: 5.5rem;
        height: .4rem;
        margin: .4rem auto 0;
        background: #103C61;
        color: #BBBBBB;
        font-size: .24rem;
        border: .02rem solid #34e5fa;
        padding: .17rem .2rem;
      }
      button {
        background: url(../assets/loginbtn.png) no-repeat;
        background-size: contain;
        width: 4rem;
        height: .72rem;
        font-size: .28rem;
        color:#fff;
      }
      p {
        font-size: .22rem;
        color: #34E5FA;
      }
    }
    .regist {
      display: flex;
      flex-direction: column;
      align-items: center;
      .common {
        width: 5.5rem;
        height: .56rem;
        margin-top: .3rem;
        display: flex;
        input {
          width:100%;
          border: .02rem solid #34e5fa;
          height: 100%;
          background: #103C61;
          color: #BBBBBB;
          font-size: .24rem;
          padding: 0 0 0 .2rem;
        }
      }
      button {
        margin-top: .2rem;
        color:#fff;
        font-size: .28rem;
        line-height: .72rem;
        width: 4rem;
        height: .72rem;
        background: url('../assets/next.png') no-repeat;
        background-size: contain;
      }
      .yz {
        display: flex;
        justify-content: space-between;
        align-items: center;
        input {
          width: 3.3rem;
        }
        img,
        span {
          width: 1.7rem;
          height: .56rem;
        }
        span {
          line-height: .56rem;
          color:#fff;
          font-size: .24rem;
          background: url('../assets/hq.png') no-repeat;
          background-size: contain;
        }
      }
    }
    /deep/ .van-tabs {
      .van-tabs__wrap {
        border: none;
        .van-tabs__nav {
          background: none!important;
          .van-tab {
            color:#BBBBBB;
          }
          .van-tab--active {
            color: #fff;
          }
          .van-tabs__line {
            background: #FFAA00;
            width: .6rem!important;
          }
        }
      }
      .van-tabs__wrap::after {
        border: none;
      }
    }

  }
}
</style>