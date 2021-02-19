<template>
  <div id="app">
    <el-card class="login-card">
      <el-form :model="loginFormData" :rules="loginFormRules" ref="loginForm" style="margin-top: 50px;">
        <el-form-item prop="mobile">
          <el-input v-model="loginFormData.mobile" placeholder="请输入您的手机号"></el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input v-model="loginFormData.password" placeholder="请输入您的密码"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" style="width: 100%;" @click="login">登录</el-button>
        </el-form-item>
      </el-form>
    </el-card>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    const checkMobile = (rule, value, callback) => {
      value.charAt(2) === '9' ? callback() : callback(new Error('第三位必须是 9 ~~'));
    };
    return {
      // 数据
      loginFormData: {
        mobile: '',
        password: '',
      },
      // 规则
      loginFormRules: {
        // !key 代表要校验的字段名
        mobile: [
          { required: true, message: '手机号不能为空', trigger: 'blur' },
          { pattern: /^1[3-9]\d{9}$/, message: '手机号格式不正确', trigger: 'blur' },
          { validator: checkMobile, trigger: 'blur' },
        ],
        password: [
          { required: true, message: '密码不能为空', trigger: 'blur' },
          { min: 6, max: 16, message: '密码的长度为 6~16 位', trigger: 'blur' },
        ],
      },
    };
  },
  methods: {
    async login() {
      const r = await this.$refs.loginForm.validate().then(r => r).catch(e => e);
      if(!r) return this.$message.error('校验失败')
      this.$message.success('校验通过')
    },
  },
};
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
.login-card {
  width: 440px;
  height: 300px;
  background-color: #fff;
}
</style>
