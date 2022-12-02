<template>
  <div class="cancel-item"> 
    <h5 class="header-item">Cancel</h5>
    <div 
    class="show-cancel-item"
    v-for="(item, index) in cancel" 
    :key="index">
      <h6>{{item.taskname}}</h6>
      <p>{{item.currentTime}}</p>
      <p style="color:red">hủy bỏ lúc:</p>
      <p style="color:red">{{`${new Date().getHours()}:${new Date().getMinutes()} ${new Date().getDate()}/${new Date().getMonth() + 1}/${new Date().getFullYear()}`}}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cancel: {},
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.cancel-item {
  width: 20vw;
  height: 90vh;
  background-color: rgb(221, 219, 219);
}
.header-item {
  background-color: white;
}
.show-cancel-item {
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  margin: 15px;
  background-color: white;
  width: 18vw;
}
</style>
