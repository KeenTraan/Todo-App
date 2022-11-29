<template>
  <div class="Todo-view">
    <Sidebar />
    <div> 
      <Search />
      <Todo />
    </div>
  </div>
</template>

<script>
import Todo from '@/components/TodoComponent/TodoComponent.vue'
import Sidebar from '@/components/SidebarComponent/SidebarComponent.vue'
import Search from '@/components/SearchComponent/SearchComponent.vue'
export default {
  components: {
    Sidebar,
    Todo,
    Search
  }
}
</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.Todo-view {
  display: flex;
  /* height: 100vh; */
  /* border: 1px solid red; */
}
</style>