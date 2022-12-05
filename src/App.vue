<template>
  <div id="app">
    <Sidebar />
    <router-view />
  </div>
</template>
<script>
import Sidebar from './components/SidebarComponent/SidebarComponent.vue';
export default {
  components: {
    Sidebar,
  }
}
</script>
<style lang="scss">
* {
  padding: 0;
  margin: 0;
}
</style>
