<template>
  <div class="login-wrap">
    <div class="lw-login-container">
      <div class="login-box">
        <div class="login-box-left">
          <img src="../assets/images/login-test.jpg" />
        </div>
        <div class="login-box-right">
          <h1>
            <img alt="" />
            <span>title</span>
          </h1>
          <!-- 登录表单  BEGIN -->
          <div class="login-form">
            <el-form
              ref="loginFormRef"
              :model="loginForm"
              :rules="logiFormRules"
            >
              <el-form-item prop="username">
                <el-input
                  v-model="loginForm.username"
                  placeholder="请输入登录名"
                  clearable
                  prefix-icon="el-icon-user"
                ></el-input>
              </el-form-item>
              <el-form-item prop="password">
                <el-input
                  v-model="loginForm.password"
                  prefix-icon="el-icon-lock"
                  placeholder="请输入密码"
                  show-password
                >
                </el-input>
              </el-form-item>
              <el-form-item>
                <el-button
                  type="primary"
                  size="mini"
                  @keyup.enter.native="loginIn"
                  >登录</el-button
                >
              </el-form-item>
            </el-form>
          </div>
          <!-- 登录表单  END -->
        </div>
      </div>
      <div class="login-footer">
        <span> 建议浏览器：IE11及以上，谷歌，Firefox，谷歌内核浏览器 </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loginForm: {
        username: "",
        password: "",
      },
      logiFormRules: {
        username: [
          {
            message: "用户名不能为空",
            trigger: "blur",
          },
          {
            min: 3,
            message: "用户名长度不小于3",
            trigger: "blur",
          },
        ],
        password: [
          {
            message: "密码不能为空",
            trigger: "blur",
          },
          {
            min: 6,
            message: "用户名长度不小于6",
            trigger: "blur",
          },
        ],
      },
    };
  },
  methods: {
    /* 登录验证 */
    loginIn() {
      this.$refs.loginFormRef
        .validate()
        .then(() => {})
        .catch((err) => err);
    },
  },
};
</script>

<style lang="scss" scoped>
.login-wrap {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  background-color: beige;
  /* login 盒子 */
  .login-box {
    display: flex;
    justify-content: flex-start;
    width: 960px;
    box-shadow: 0 10px 30px 0 rgba(13, 31, 101, 0.2);
    /* 左侧banner */
    .login-box-left {
      width: 50%;
      img {
        width: 100%;
        height: 100%;
      }
    }
    /*  右侧 login form */
    .login-box-right {
      width: 50%;
      h1 {
        width: 100%;
        height: 48px;
        padding-top: 10px;
        text-align: center;
        line-height: 48px;
        font: 26px 700 "song";
        color: #303133;
      }
      /*登录表单 */
      .login-form {
        margin: 50px 0 0 70px;
        .el-input,
        .el-button {
          width: 80%;
        }
      }
    }
  }
  /* footer  文字 */
  .login-footer {
    position: relative;
    top: 25px;
    width: 100%;
    font-size: 14px;
    color: #0d618f;
    line-height: 18px;
    text-align: center;
  }
}
</style>
