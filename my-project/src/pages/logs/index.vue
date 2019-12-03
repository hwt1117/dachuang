<template>
  <div class="main">
    <div class="title">已经为您展示 <div style="font-size:18px"> &#160;{{address}} &#160;</div> 附近所有银行:</div>
    <div class="login">
      <div class="dneglu" v-for="(item,index) in bank" :key="index">{{index+1}}.{{item.name}}({{item.juli}})</div>
    </div>
  </div>
</template>

<script>
import card from "@/components/card";
import QQMapWX from "../../utils/qqmap-wx-jssdk.min";
export default {
  data() {
    return {
      address:"null",
      bank: [
        {
          "name": "塔大银行",
          "juli": "200米内"
        },
        {
          "name": "建设银行",
          "juli": "桃园步行街内"
        },
        {
          "name": "中国银行",
          "juli": "上海风情街内"
        },
        {
          "name": "中国工商银行",
          "juli": "领先商业街内"
        },
        {
          "name": "中国农业银行",
          "juli": "金色家园内"
        }
      ]
    };
  },

  components: {
    card
  },

  methods: {
    //  获取用户地址
    getLocation() {
      let _this = this;
      wx.getLocation({
        type: "wgs84",
        success(res) {
          console.log(res, "地址");
          const lat = res.latitude;
          const lon = res.longitude;
          _this.getLocal(lat, lon);
        }
      });
    },
    getLocal(lat, lon) {
      let qqmapsdk = new QQMapWX({
        key: "LVVBZ-B456F-ZLNJF-NRVMB-76M2K-H3BXS"
      });
      qqmapsdk.reverseGeocoder({
        location: {
          latitude: lat,
          longitude: lon
        },
        success:(res)=> {
          
          console.log(res, "success");
          let address = res.result.address_component
          console.log(address)
          this.address = address.city+address.district
          console.log(this.address)
        },
        fail: function(res) {
          console.log(res, "fail");
        }
      });
    }
  },

  created() {
    // let app = getApp()
    this.getLocation();
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
  padding-top: 10%;
  /* border: 1px solid black; */
  /* background-color: #f5f5f5; */
}
.dneglu {
  /* border: 1px solid black; */

  margin-left: 10%;
  height: 30px;
  width: 100%;
  display: flex;
  /* justify-content: center; */
  align-items: center;
  font-size: 16px;
}
.login {
  padding-top: 10%;

  width: 100%;
  height: 300px;
  /* border: 1px solid black; */
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.title {
  display: flex;
  align-items: center
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
