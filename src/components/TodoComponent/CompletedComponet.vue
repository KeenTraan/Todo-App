<template>
  <div class="completed-item">
    <h4 class="text">Completed</h4>
    <div
      class="show-item-completed"
      v-for="(item, index) in completed"
      :key="index"
    >
      <h5>{{ item.taskname }}</h5>
      <p>{{ item.currentTime }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "CompletedTodo",
  props: {
    completed: {},
  },
};
</script>

<style scoped>
.completed-item {
  background-color: rgb(221, 219, 219);
  width: 20vw;
  height: 90vh;
}
.text {
  background-color: white;
}
.show-item-completed {
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  padding: 5px;
  margin: 15px;
  background-color: white;
  width: 18vw;
}
</style>
