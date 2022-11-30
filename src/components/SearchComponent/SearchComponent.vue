<template>
  <nav class="navbar">
  <div class="container-fluid">
    <form class="d-flex" role="search">
      <input class="form-control me-2" type="search" placeholder="Enter Task" aria-label="Search" @input="searchItem" >
      <button class="btn btn-outline-success" type="submit">Search</button>
    </form>
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
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
</style>