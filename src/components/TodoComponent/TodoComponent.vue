<template>
  <div>
    <SideBar />
    <div class="content">
      <div class="item-list">
        <div class="add-item">
          <h4 class="text">New</h4>
          <div class="input-form" v-show="ishiden">
            <input
              type="text"
              name="input"
              placeholder="Enter New Task"
              v-model="input_content"
            />
            <br />
            <p style="margin-left: 1rem">{{ `${hours} ${date}` }}</p>
            <button
              :disabled="this.input_content === ''"
              class="btn-save"
              @click="handleAddItem"
            >
              lưu
            </button>
            <button class="btn-cancel">hủy bỏ</button>
          </div>
          <div class="todo-list">
              <div
                class="show-item"
                v-for="(item, index) in todoList"
                :key="index"
              >
                <h5 style="margin-left: 1rem">{{ item.taskname }}</h5>
                <p style="margin-left: 1rem">{{ item.currentTime }}</p>
                <button class="btn-save" @click="handleCompleted(index)">
                  hoàn thành
                </button>
                <button class="btn-cancel" @click="handleCancel(index)">
                  từ bỏ
                </button>
              </div>
          </div>
        </div>
      </div>
      <div class="btn">
        <button type="submit" class="btn-add" @click="ishiden = !ishiden">
          Thêm Mới
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoComponent",
  data() {
    return {
      date: "",
      hours: "",
      ishiden: false,
      input_content: "",
      todoList: [],
    };
  },
  methods: {
    handleAddItem() {
      const time = `${new Date().getHours()}:${new Date().getMinutes()}`;
      const todoAdd = {
        taskname: this.input_content,
        currentTime: time,
      };
      this.todoList = [...this.todoList, todoAdd];
      localStorage.setItem("todoList", JSON.stringify(this.todoList));
      this.input_content = "";
    },
  },
  mounted() {
    localStorage.setItem("todoList", JSON.stringify([]));
    this.todoList = JSON.parse(localStorage.getItem("todoList") ?? []);

    setInterval(() => {
      const time = `${new Date().getHours()}:${new Date().getMinutes()}:${new Date().getSeconds()}`;
      const date = `${new Date().getDate()}/${
        new Date().getMonth() + 1
      }/${new Date().getFullYear()}`;
      this.hours = time;
      this.date = date;
    }, 1000);
  },
};
</script>

<style lang="scss" scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.content {
  background-color: rgb(220, 220, 220);
  width: 21vw;
  height: 90vh;
  position: relative;
  top: 1.5rem;
  box-shadow: 1px 1px 10px;
  .item-list {
    display: flex;
    justify-content: center;
    .text {
      background-color: white;
      width: 21vw;
      margin-left: 1px;
    }
    .input-form {
      border-radius: 5px;
      margin-top: 1rem;
      margin-left: 1rem;
      background-color: white;
      width: 18vw;
      input {
        position: relative;
        width: 90%;
        border-radius: 0.5rem;
        margin: 1rem;
      }
    }
  }
  .add-item {
    display: flex;
    flex-direction: column;
    .btn-save {
      background-color: green;
      color: white;
      border: none;
      border-radius: 3px;
      margin: 4px 8px 4px 8px;
      padding: 4px 8px 4px 8px;
    }
    .btn-cancel {
      background-color: red;
      color: white;
      border-radius: 3px;
      border: none;
      float: right;
      margin: 4px 8px 4px 8px;
      padding: 4px 8px 4px 8px;
    }
  }
  .btn {
    .btn-add {
      position: absolute;
      bottom: 10px;
      left: 2.5rem;
      width: 15rem;
      border-radius: 0.5rem;
      border: 0.5px solid green;
    }
  }
  .btn-add:hover {
    background-color: green;
  }
  .todo-list {
    margin-top: 0.5rem;
    .show-item {
      margin: 15px;
      border-radius: 5px;
      margin-left: 1rem;
      background-color: white;
      width: 18vw;
    }
  }
  .scroll-bar {
    height: 60vh;
  }
  .scroll-bar::-webkit-scrollbar {
    width: 10px;
  }
  .scroll-bar::-webkit-scrollbar-thumb {
    background-color: white;
    border-radius: 100rem;
  }
  .scroll-bar::-webkit-scrollbar-track {
    background-color: grey;
    border-radius: 100rem;
  }
}
</style>
