<template>
  <div class="Todo-view">
    <Sidebar />
    <div class="body">
      <Search />
      <div class="item-list">
        <AddItem />
      </div>
    </div>
  </div>
</template>

<script>
import AddItem from '@/components/TodoComponent/AddItemComponent.vue'
import Sidebar from '@/components/SidebarComponent/SidebarComponent.vue'
import Search from '@/components/SearchComponent/SearchComponent.vue'
export default {
  components: {
    Sidebar,
    AddItem,
    Search
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