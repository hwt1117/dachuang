<template>
  <div class="main">
    <div class="login">
      <div class="dneglu">登陆</div>
      <div>
        <div class="username">
          <label for="username" class="ulable">用户名:</label>

          <input type="text" class="input" id="username" />
        </div>
        <div class="username">
          <label for="password" class="ulable">密码:</label>
          <input type="password" class="input" id="password" />
        </div>
      </div>

      <div class="button">
        <button @click="navigate()">登陆</button>
        <button>注册</button>
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
  font-size: 20px;
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
}
.input {
  width: 200px;
  border: 1px solid rgba(255, 102, 62, 1);
  margin-right: 50px;
}
.button {
  height: 50px;
  width: 100%;
  display: flex;
  justify-content: center;
}
</style>
