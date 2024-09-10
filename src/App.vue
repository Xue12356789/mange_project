<script lang="ts" setup>
import { ref } from 'vue'
import axios from 'axios'
const mima_input = ref('')
const account_input = ref('')
 
const http = axios.create({
  baseURL: '/api'
});



// 登录提交按钮
const loginSubmit = ()=> {
  const user = account_input.value;
  const password = mima_input.value;

  // 简单的输入验证
  if (!user || !password) {
    alert("用户名和密码不能为空");
    return;
  }

  // axios.post("http://192.168.31.17:80/login/login-submit", {
  //               user: user,
  //               password: password,
  //           })
  // .then(res => {
  //     console.log(res);
  // })
  // .catch();
  http.post("login/login-submit", {
                user: user,
                password: password,
            }
  )
  .then(res => {
      console.log(res);
  })
  .catch();

}

</script>

<template>
  <video autoplay muted loop id="bg-video">
    <source src="../public/index-background.mp4" type="video/mp4">
  </video>
  <!-- 登陆页面 -->
  <div class="login-mian">
    <span class="login-title">系统大数据平台</span>
    <div class="index-input">
      <img src="../src/assets/img/人数.png" width="15px" height="15px" alt="账号">
      <el-input type="text" v-model="account_input" placeholder="请输入账号" clearable validate-event >
      </el-input>
    </div>
    <div class="index-input">
      <img src="../src/assets/img/锁.png" width="15px" height="15px" alt="密码">
      <el-input type="password" v-model="mima_input" placeholder="请输入密码" show-password>
      </el-input>
    </div>
    <button class="login-botton" @click="loginSubmit">登录</button>
  </div>
</template>

<style scoped lang="less">
.login-mian {
  position: relative;
  width: 20%;
  height: 40%;
  min-height: 390px;
  box-shadow: 0 0 0.5vw #06fcfa inset;
  background: 
  linear-gradient(#06fcfa, #06fcfa) left top,
  linear-gradient(#06fcfa, #06fcfa) left top,
  linear-gradient(#06fcfa, #06fcfa) right top,
  linear-gradient(#06fcfa, #06fcfa) right top,
  linear-gradient(#06fcfa, #06fcfa) left bottom,
  linear-gradient(#06fcfa, #06fcfa) left bottom,
  linear-gradient(#06fcfa, #06fcfa) right bottom,
  linear-gradient(#06fcfa, #06fcfa) right bottom;
  background-repeat: no-repeat;
  background-size: 0.1vw 0.8vw, 0.8vw 0.1vw;
  padding:2px;   
  position: absolute; /* 使用绝对定位 */
  top: 45%; /* 上边界距离父容器顶部50% */
  left: 50%; /* 左边界距离父容器左侧50% */
  transform: translate(-50%, -50%); /* 使用 transform 属性来向左上方移动自身宽高的一半 */
}

.login-title {
  color: #06f3f2;
  font-size: 20px;
  display: flex;
  justify-content: center;
  letter-spacing: 3px;
  margin: 8%;
  font-weight: bold;
}

.index-input {
  margin: 0 0 30px 0;
  height: 50px;
  width: 80%;
  position: relative;
  top: 10%;
  left: 50%;
  transform: translate(-50%, -50%);
  border-bottom:1px solid #06f3f2;
  padding: 0 0 20px 0;
}

.el-input {
  padding: 10px;
  border: none;
  /* 去除默认边框 */
  font-size: 16px;
  width: 95%;
  box-sizing: border-box;
  /* 让 padding 不会撑大输入框 */
  outline: none;
}
 
:deep(.el-input__inner){
    color: #06f3f2 !important; /* 设置占位符的字体颜色 */
    border:1px solid rgba(0, 0, 0, 0);
    background-color:rgba(0, 0, 0, 0);
    &::placeholder{
      color: #407777 !important; /* 设置占位符的字体颜色 */
    }
}
:deep(.el-input .el-input__clear) {
  margin: 0 10px 0 0 ;
  color: #06f3f2;
}

.login-botton {
  width: 80%;
  height: 15%;
  position: relative;
  top: 10%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 20px;
  background-color: #06f3f2;
  color: aliceblue;
}
</style>
