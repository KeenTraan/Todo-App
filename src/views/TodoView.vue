<template>
  <div class="Todo-view">
    <Sidebar />
    <Todo />
  </div>
</template>

<script>
import Todo from '@/components/TodoComponent/TodoComponent.vue'
import Sidebar from '@/components/SidebarComponent/SidebarComponent.vue'
export default {
  components: {
    Sidebar,
    Todo
  }
}
</script>

<style scoped>
.Todo-view {
  display: flex;
}
</style>