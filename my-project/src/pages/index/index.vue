<template>
  <div class="main">
    <div class="login">
      <div class="dneglu"><b>登陆</b></div>
      <div>
        <div class="username">
          <label for="username" class="ulable"><b>用户名:</b></label>

          <input type="text" class="input" id="username" placeholder="请输入用户名" />
        </div>
        <div class="username">
          <label for="password" class="ulable">密码:</label>
          <input type="password" class="input" id="password" placeholder="请输入密码"/>
        </div>
      </div>

      <div class="button">
        <button @click="navigate()"  style="height:50px;width:40%;color:#5c89ff"><b>登陆</b> </button>
        <button  style="height:50px;width:40%;color:#5c89ff">注册</button>
      </div>
    </div>
  </div>
</template>

<script>
import card from "@/components/card";
import QQMapWX from "../../utils/qqmap-wx-jssdk.min";
export default {
  data() {
    return {};
  },

  components: {
    card
  },

  mounted() {
    // let app = getApp()
  },
  methods: {
    navigate() {
      let url = "../log/main";
      wx.navigateTo({ url });
    },
    
  }
};
</script>

<style scoped>
* {
  box-sizing: border-box;
  /* background-color: #f5f5f5;/ */
}
.main {
  box-sizing: border-box;
  height: 500px;
  width: 100%;
  /* border: 1px solid black; */
  /* background-color: #f5f5f5; */
  display: flex;
  justify-content: center;
  align-items: center;
}
.dneglu {
  /* border: 1px solid black; */
  height: 30px;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 28px;
  font-weight: 400;
}
.login {
  width: 100%;
  height: 300px;
  /* border: 1px solid black; */
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.username {
  height: 50px;
  width: 100%;
  /* background-color: antiquewhite; */
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: flex-end;
}
.ulable {
  /* border: 1px solid black; */
  margin-right: 20px;
  font-size: 18px;
  font-weight: 400;

}
.input {
  width: 200px;
  height: 30px;
  border: 1px solid #5C89FF;
  border-radius: 5px;
  margin-right: 50px;
  padding-left: 5px;
}
.button {
  height: 50px;
  width: 100%;
  display: flex;
  justify-content: center;
}
</style>
