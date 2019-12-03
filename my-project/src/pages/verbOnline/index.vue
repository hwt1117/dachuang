<template>
  <div>
    <p>业务类型：</p>
    <p>当前等候人数：</p>
    <p>与银行联系</p>
    <button @click="godetails(3)">预约</button>
  </div>
</template>

<script>
export default {
  methods: {
    godetails(time) {
      const url = "/pages/remind/main?time="+time;
      wx.navigateTo({url});
    }
  }
};
</script>

<style>
</style>