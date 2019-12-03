<template>
  <div>
    <p class="title header">您的预约服务</p>
    <p
      class="time header"
    >预计时间还剩:{{hour? hourString+':'+minuteString+':'+secondString : minuteString+':'+secondString}}</p>
    <button @click="back" style="color:#5C89FF;width:60%;margin-top:130px;">取消</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      hour: "",
      minute: "",
      second: "",
      promiseTimer: "",
      remainTime: 3 //设置时间
    };
  },
  computed: {
    hourString() {
      return this.formatNum(this.hour);
    },
    minuteString() {
      return this.formatNum(this.minute);
    },
    secondString() {
      return this.formatNum(this.second);
    }
  },

  methods: {
    back() {
      wx.navigateBack({
        delta: 1,
        success: () => {
          console.log("success");
          clearInterval(this.promiseTimer);
        },
        fail: () => {
          console.log("fail");
        }
      });
    },

    countDowm() {
      var self = this;
      clearInterval(this.promiseTimer);
      this.promiseTimer = setInterval(function() {
        if (self.hour === 0) {
          if (self.minute !== 0 && self.second === 0) {
            self.second = 59;
            self.minute -= 1;
          } else if (self.minute === 0 && self.second === 0) {
            self.second = 0;
            self.$emit("countDowmEnd", true);
            clearInterval(self.promiseTimer);
            const url = "/pages/pingjia/main";
            wx.navigateTo({ url });
          } else {
            self.second -= 1;
          }
        } else {
          if (self.minute !== 0 && self.second === 0) {
            self.second = 59;
            self.minute -= 1;
          } else if (self.minute === 0 && self.second === 0) {
            self.hour -= 1;
            self.minute = 59;
            self.second = 59;
          } else {
            self.second -= 1;
          }
        }
      }, 1000);
    },
    formatNum(num) {
      return num < 10 ? "0" + num : "" + num;
    }
  },
  onLoad(options) {
    if (this.remainTime > 0) {
      this.hour = Math.floor((this.remainTime / 3600) % 24);
      this.minute = Math.floor((this.remainTime / 60) % 60);
      this.second = Math.floor(this.remainTime % 60);
      this.countDowm();
    }
  }
};
</script>

<style>
.header {
  width: 100%;
  font-size: 20px;
  /* margin-left: 10%;  */
  margin-bottom: 5%;
  text-align: center;
}
.title {
  margin-top: 100px;
}
</style>