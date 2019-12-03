<template>
  <div>
    <p>业务类型：{{Info.yewu}}</p>
    <p>当前等候人数：{{Info.people}}</p>
    <a>与银行联系{{Info.chat}}</a>
    <button @click="godetails(3)">预约</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      Info: { 
        yewu: "存款",
        people:"10",
        chat:"1001234567"
       }
    };
  },
  methods: {
    godetails(time) {
      const url = "/pages/remind/main?time=" + time;
      wx.navigateTo({ url });
    }
  }
};
</script>

<style>
</style>