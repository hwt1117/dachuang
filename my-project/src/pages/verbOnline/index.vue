<template>
  <div>
    <p class="title header">业务类型：{{Info.yewu}}</p>
    <p class="people header">当前等候人数：{{Info.people}}</p>
    <a class="getconnect header">与银行联系{{Info.chat}}</a>
    <button style="color:#5C89FF;width:60%;margin-top:130px;" @click="godetails(3)">预约</button>
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
.header{
  font-size: 20px;
  /* margin-left: 10%;  */
  margin-bottom: 5%;
  text-align: center;
}
.title{
  margin-top: 100px;
}
</style>