<template>
  <div class="sidebar">
    <h3 class="header-sidebar">Basic Exercise</h3>
    <ul>
      <li
        class="menu-list" 
        v-for="item in menuList"
        :key="item.id"
        :class="[isActiveMenu(item.name) && 'active']"
      >
        <router-link :to="item.link" style="text-decoration: none;">
          {{ item.label }}
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "SibarComponent",
  data() {
    return {
      menuList: [
        {
          id: 1,
          label: "Trang Chủ",
          name: "Homepage",
          link: "/",
        },
        {
          id: 2,
          label: "Todo App",
          name: "TodoApp",
          link: "/todoapp",
        },
        {
          id: 3,
          label: "Bài 2",
          name: "LessionTwo",
          link: "/lesson2",
        },
        {
          id: 4,
          label: "Bài 3",
          name: "LessionThree",
          link: "/lesson3",
        },
      ],
    };
  },
  computed: {
    isActiveMenu() {
      return (menuName) => {
        return this.$route.name === menuName;
      };
    },
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  position: relative;
}
.sidebar {
  background-color: rgb(220,220,220);
  margin-right: 5rem;
  height: 100vh;
  width: 15vw;
  text-align: center;
}
.menu-list {
  list-style: none;
  font-size: larger;
}
</style>
