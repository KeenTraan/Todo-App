<template>
  <div id="TodoApp">
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
              <p style="margin-left: 1rem">{{ item }}</p>
              <p style="margin-left: 1rem">{{ `${hours} ${date}` }}</p>
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
      <button type="submit" class="btn-add" @click="ishiden = !ishiden">
        Thêm Mới
      </button>
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
      hours: `${new Date().getHours()}:${new Date().getMinutes()}`,
      ishiden: false,
      input_content: "",
      todoList: [],
    };
  },
  methods: {
    handleAddItem(e) {
      e.preventDefault();
      
    },
  },
};
</script>

<style lang="scss" scoped>
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.content {
  background-color: rgb(220, 220, 220);
  width: 21vw;
  height: 100vh;
  position: relative;
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
      background-color: rgb(0,128,0);
      border: none;
      border-radius: 3px;
      margin: 5px 5px 5px 15px;
    }
    .btn-cancel {
      background-color: rgb(255,0,0);
      border-radius: 3px;
      border:none;
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
      margin-left: 1rem;
      background-color: white;
      width: 18vw;
    }
  }
}
</style>
