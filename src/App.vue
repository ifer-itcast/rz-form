<template>
  <div id="app">
    <el-card class="login-card">
      <el-form :model="loginFormData" style="margin-top: 50px;">
        <el-form-item>
          <el-input v-model="loginFormData.mobile" placeholder="请输入您的手机号"></el-input>
        </el-form-item>
        <el-form-item>
          <el-input v-model="loginFormData.password" placeholder="请输入您的密码"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" style="width: 100%;">登录</el-button>
        </el-form-item>
      </el-form>
    </el-card>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      // 数据
      loginFormData: {
        mobile: '',
        password: ''
      },
    }
  }
}
</script>

<style>
#app {
  width: 100%;
  height: 100vh;
  background-color: pink;
  display: flex;
  justify-content: center;
  align-items: center;
}
.login-card{
  width: 440px;
  height: 300px;
  background-color: #fff;
}
</style>
