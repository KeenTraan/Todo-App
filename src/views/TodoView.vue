<template>
  <div class="Todo-view">
    <Sidebar />
    <div class="body">
      <div class="item-list">
        <TodoApp />
      </div>
    </div>
  </div>
</template>

<script>
import TodoApp from '@/components/TodoComponent/TodoAppComponent.vue'
import Sidebar from '@/components/SidebarComponent/SidebarComponent.vue'
export default {
  components: {
    Sidebar,
    TodoApp,
  }
}
</script>

<style scoped>
.Todo-view {
  display: flex;
}
.body {
  display: flex;
  flex-direction: column;
}
.item-list {
  display: flex;
}
</style>