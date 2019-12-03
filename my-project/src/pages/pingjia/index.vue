<template>
  <div class="main">
    
      <textarea name id cols="30" rows="10" placeholder="请输入你的评价内容......"></textarea>
      <button type="button" style="height:50px;width:100%;color:#5c89ff">提交</button>
    </div>
</template>

<script>
export default {
  data() {
    return {
      
    }
  },
};
</script>

<style>
.main {
  width: 100%;
  height: 500px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  
}
textarea {
  box-sizing: border-box;
  width: 95%;
  height: 300px;
  border: 1px solid #5c89ff;
  border-radius: 20px;
  padding:10px;
}
</style>