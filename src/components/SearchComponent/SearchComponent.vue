<template>
  <nav class="navbar">
  <div class="container-fluid">
    <div class="d-flex" role="search">
      <input class="form-control me-2" type="search" placeholder="Enter Task" aria-label="Search" @input="searchItem" style="margin-right:10px">
      <button class="btn btn-outline-success" type="submit">Search</button>
    </div>
  </div>
</nav>
</template>

<script>
// import TodoApp from '@/views/TodoAppView.vue'
export default {
  name: "searchBar",
  methods: {
    searchItem(event) {
      this.$emit('query', event.target.value);
    }
  },
}
</script>

<style scoped>
*{
  margin: 0;
  padding: 0;
}
.navbar {
  margin-top: 10px;
}
</style>