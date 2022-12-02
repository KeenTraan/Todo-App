<template>
  <div class="completed-item">
    <h5 class="header-item">Completed</h5>
    <div
      class="show-item-completed"
      v-for="( item, index ) in completed"
      :key="index"
    >
      <h6>{{ item.taskname }}</h6>
      <p>{{ item.currentTime }}</p>
      <p style="color:green">hoàn thành lúc:</p>
      <p style="color:green">{{`${new Date().getHours()}:${new Date().getMinutes()} ${new Date().getDate()}/${new Date().getMonth() + 1}/${new Date().getFullYear()}`}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "CompletedTodo",
  data() {
    return {

    }
  },
  props: {
    completed: {}, //data trong todolist duoc lay ra 
  },
}
</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.completed-item {
  background-color: rgb(221, 219, 219);
  width: 20vw;
  height: 90vh;
  margin-right: 3rem;
}
.header-item {
  background-color: white;
}
.show-item-completed {
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  margin: 15px;
  background-color: white;
  width: 18vw;
}
</style>
