<template>
  <div>
    <header>
      <span class="glyphicon glyphicon-chevron-left" @click="gotopage"></span>
      <span>手机快捷登录</span>
    </header>
    <div class="container">
      <form class="login-form">
        <ul>
          <li class="country-choose-box">
            <div class="input-box">
              <label>
                <span class="country-name">中国大陆</span>
                <span class="fr" @click="showCountry">+86</span>
              </label>
            </div>
          </li>
          <li class="tel-num-box">
            <div class="input-box">
              <label>
                <input type="tel" name="" placeholder="手机号码" maxlength="11">
              </label>
            </div>
          </li>
          <li class="password-box">
            <div class="input-box">
              <label>
                <input type="" name="" placeholder="动态密码">
                <span class="password">获取动态密码</span>
              </label>
            </div>
          </li>
          <li class="login-box">
            <div class="login-input-box">
              <a href=""><span class="login-btn">登录</span></a>
            </div>
          </li>
          <li class="choose-box">
            <div class="choose-input-box">
              <span class="login-btn">或</span>
            </div>
          </li>
          <li class="way-box">
            <div class="way-input-box">
              <a href=""><span class="login-btn">账号登录</span></a>
            </div>
          </li>
        </ul>
      </form>           
    </div>
    <footer>
      <div class="login-api container">
        <ul class="login-list">
          <li class="qq">
            <a href="https://jifen.qq.com/pc/login?s_url=">
              <img src="../assets/qq.png" width="32px" height="32px">
            </a>
          </li>
          <li class="weibo">
            <a href="https://api.weibo.com/">
              <img src="../assets/weibo.png" width="38px" height="38px">
            </a>
          </li>
          <li class="paly">
            <a href="https://auth.alipay.com/">
              <img src="../assets/paly.png" width="32px" height="32px">
            </a>
          </li>
          <li class="taobao">
            <a href="https://taobao.com/">
              <img src="../assets/taobao.png" width="36px" height="36px">
            </a>
          </li>
        </ul>
      </div>
      <div class="remind-new">
        <span class="no-count">还没有账号？
          <span @click="gotoreg">
            <a href="">立即注册</a>
          </span>
        </span>
      </div>
    </footer>
    <my-dialog :is-show="isShowCountryDialog" @on-close="closeDialog('isShowCountryDialog')">
      <country-tel></country-tel>
    </my-dialog>
  </div>
</template>

<script>
import Dialog from './dialog'
import CountryTel from './country'
export default {
  components: {
    MyDialog: Dialog,
    CountryTel
  },
  data () {
    return {
      isShowCountryDialog: false
    }
  },
  methods: {
    gotopage () {
      this.$router.push({path: '/'})
    },
    gotoreg () {
      this.$router.push({path: '/register'})
      alert(5)
    },
    showCountry () {
      this.isShowCountryDialog = true
    },
    closeDialog (attr) {
      this[attr] = false
    }
  }
}
</script>
<style scoped>
  header {
    height: 50px;
    color: #333;
    font-size: 18px;
    width: 100%;
    text-align: center;
    line-height: 50px;
    position: relative;
    margin-bottom: 20px;
  }
  .glyphicon-chevron-left {
      position: absolute;
      left: 5%;
      top:15px;
  }
   ul{
    padding: 2px 5%;
  }
  ul li {
    list-style: none;
    height: 44px;
    padding: 0 15px;
    margin: 5px 0;
  }
  .input-box {
    border: 1px solid #f1f1f1;
    border-radius: 25px;
    height: 90%;
    line-height: 90%;
    position: relative;
  }
  .input-box label {
    height: 46px;
    margin: 5px 0;
  }
  .input-box input {
    border: 1px solid transparent;
    border-radius: 25px 0 0 25px;
    border-right: 0;
    height: 80%;
    width: 150%;
    line-height: 90%;
    position: relative;
    top: -4px;
    font-weight: normal;
    outline: none;
    padding-left: 20px;
    color: #333;
  }
  label span{
    color: #333;
    font-weight: normal;
  }
  span.country-name,span.tel-num, span.get-psw {
    position: relative;
    top:8px;
    padding-left: 20px;
    font-size: 16px;
  }
  span.tel-num, span.get-psw, span.password {
    color: #ccc;
  }
  .fr {
    position: absolute;
    right: 0;
    top:10px;
    right: 35px;
    cursor: pointer;
  }
  .input-box .fr::after {
    content: '';
  /*  height: 0;*/
    border-left: 5px solid transparent;
    border-right: 5px solid transparent;
    border-top: 5px solid #666;
    position:absolute;
    top:4px;
    margin-left: 5px;
  }
  .password {
    position: absolute;
    right: 0;
    top:10px;
    right: 20px; 
  }
  .login-input-box {
    display: block;
    height: 100%;
    background-color: #2692ff;
    border-radius: 25px;       
  }
  .login-input-box a {
    display: block;
    height: 100%;
    text-align: center;
    color: #fff;
    font-size: 18px;
  }
  span.login-btn {
    position: relative;
    top:10px;
  }
  .way-input-box {
    display: block;
    height: 100%;
    background-color: #fff;
    border-radius: 25px; 
    border: 1px solid #2692ff;
  }
  .choose-input-box span {
    display: block;
    text-align: center;
    color: #ccc;
  }
  .way-input-box a {
    display: block;
    height: 100%;
    text-align: center;
    color: #2692ff;
    font-size: 18px;
  }
  footer {
    position: absolute;
    bottom: 0;
    width: 100%;
    height: 118px;
  }
  .login-api ul {
    padding: 0 20px 0 40px;
  }
  .login-api ul li {
    display: inline-block;
    width: 22%;
    text-align: center;
  }
  .remind-new {
    text-align: center;
  }
  span.no-count {
    color: #c5c9d2;
  }
  .remind-new span a {
    color:#666;
  }
  a {
    text-decoration: none;
  }
</style>
