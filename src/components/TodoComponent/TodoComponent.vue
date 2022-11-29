<template>
  <div id="TodoApp">
    <div class="content">
      <div class="item-list">
        <div class="add-item">
          <h4 class="text">Mới</h4>
          <div class="input-form" v-show="ishiden">
            <input
              type="text"
              name="input"
              placeholder="Enter New Task"
              v-model="input_content"
            />
            <br />
            <p style="margin-left: 1rem">{{ `${hours}:${minute} ${date}` }}</p>
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
            <!-- <CardTodo v-for="(item, index) in todoList" :key="index" @onSave="handleCompleted"></CardTodo> -->
            <div
              class="show-item"
              v-for="(item, index) in todoList"
              :key="index"
            >
              <p style="margin-left: 1rem">{{ item }}</p>
              <p style="margin-left: 1rem">
                {{ `${currentHours}:${currentMinute} ${date}` }}
              </p>
              <button class="btn-save" @click="handleCompleted(index)">
                hoàn thành
              </button>
              <button class="btn-cancel" @click="handleCancel(index)">
                từ bỏ
              </button>
            </div>
          </div>
          <button type="submit" class="btn-add" @click="ishiden = !ishiden">
            Thêm Mới
          </button>
        </div>

        <div class="completed-iteam">
          <div class="completed-item-scroll"> 
            <h4 class="text">Đã Hoàn Thành</h4>
            <div
              v-for="(item, index) in completed"
              :key="index"
              class="completed-item-list"
            >
              <h6>{{ item }}</h6>
              <p>{{ `${hours}:${minute} ${date}` }}</p>
              <p style="color: green">Đã hoàn thành lúc:</p>
              <p style="color: green">
                {{ `${currentHours}:${currentMinute} ${date}` }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoComponent",
  data() {
    return {
      date: `${new Date().getDate()}/${
        new Date().getMonth() + 1
      }/${new Date().getFullYear()}`,
      currentHours: new Date().getHours(),
      currentMinute: new Date().getMinutes(),
      hours: "",
      minute: "",
      ishiden: false,
      input_content: "",
      todoList: JSON.parse(localStorage.getItem("Todo")),
      completed: JSON.parse(localStorage.getItem("Completed")),
    };
  },
  methods: {
    handleAddItem() {
      if (Array.isArray(this.todoList)) {
        this.todoList.push(this.input_content);
        this.input_content = "";
      } else {
        this.todoList = [this.input_content];
        this.input_content = "";
      }
      localStorage.setItem("Todo", JSON.stringify(this.todoList));
    },
    handleCompleted(index) {
      const completedTask = this.todoList[index];
      if (Array.isArray(this.completed)) {
        this.completed.push(completedTask);
      } else {
        this.completed = [completedTask];
      }
      this.todoList = this.todoList.filter((task, i) => i != index);
      localStorage.setItem("Todo", JSON.stringify(this.todoList));
      localStorage.setItem("Completed", JSON.stringify(this.completed));
    },
  },
  mounted: function () {
    setInterval(() => {
      const currentTime = new Date();
      this.minute = currentTime.getMinutes();
      this.hours = currentTime.getHours();
    }, 3000);
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
  display: flex;
  background-color: rgb(220, 220, 220);
  width: 20vw;
  height: 100vh;
  box-shadow: 1px 1px 10px;
  .item-list {
    display: flex;
    position: relative;
    justify-content: center;
    .text {
      background-color: white;
      width: 20vw;
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
      cursor: pointer;
      background-color: rgb(0, 128, 0);
      border: none;
      border-radius: 3px;
      margin: 5px 5px 5px 15px;
    }
    .btn-cancel {
      cursor: pointer;
      background-color: rgb(255, 0, 0);
      border-radius: 3px;
      border: none;
      float: right;
      margin: 5px 15px 5px 5px;
    }
  }
  .btn-add {
    position: absolute;
    bottom: 10px;
    left: 2.5rem;
    width: 15rem;
    border-radius: 1rem;
    border: none;
  }
  .btn-add:hover {
    background-color: green;
  }
  .todo-list {
    margin-top: 2rem;
    overflow: auto;
    height: 60vh;
    .show-item {
      margin: 15px;
      border-radius: 5px;
      background-color: white;
      width: 18vw;
    }
  }
  .completed-iteam {
    box-shadow: 1px 1px 10px;
    margin-left: 2rem;
    background-color: rgb(220, 220, 220);
    width: 22vw;
    height: 100vh;
    .completed-item-scroll {
      overflow: auto;
      height: 100vh;
      .completed-item-list {
        background-color: white;
        margin: 15px;
        border-radius: 5px;
      }
    }
  }
}
</style>
