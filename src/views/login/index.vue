<template>
  <div class="login">
    <van-cell-group>
      <van-nav-bar title="登录" class="page-nav-bar" />
      <van-form @submit="onSubmit">
        <van-field
          name="用户名"
          placeholder="请输入用户名"
          v-model="user.mobile"
        >
          <i slot="left-icon" class="iconfont icon-shouji"></i>
        </van-field>
        <van-field name="验证码" placeholder="请输入验证码" v-model="user.code">
          <i slot="left-icon" class="iconfont icon-yanzhengma"></i>
          <template #button>
            <van-button size="small" type="primary">发送验证码</van-button>
          </template>
        </van-field>
        <div style="margin: 16px">
          <van-button round block type="info" native-type="submit"
            >提交</van-button
          >
        </div>
      </van-form>
    </van-cell-group>
  </div>
</template>

<script>
import { login } from "@/api/user";
export default {
  name: "login",
  data() {
    return {
      user: {
        mobile: "",
        code: "",
      },
    };
  },
  methods: {
    async onSubmit() {
      const user = this.user;
      const res = await login(user);
      console.log(res);
    },
  },
};
</script>

<style lang="less" scoped>
// .login {
//   font-size: 60px;
// }
</style>
<style lang="less">
.page-nav-bar {
  background-color: #0f84ff;
  .van-nav-bar__title {
    color: #fff;
  }
}
</style>
