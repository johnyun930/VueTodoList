<style>
body {
  text-align: center;
  background-color: #f6f6f8;
}
input {
  border-style: groove;
}

.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>

<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:add-List="addTodo"></TodoInput>
    <TodoList
      v-bind:todoItems="todoItems"
      v-on:remove-List="removeTodo"
      v-on:remove-all="clear"
    ></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";
import TodoFooter from "./components/TodoFooter.vue";

export default {
  data() {
    return {
      todoItems: []
    };
  },
  created() {
    this.getList();
  },
  methods: {
    addTodo(item) {
      console.log(item);
      if (item !== "") {
        console.log("hello");
        let value = item && item.trim();
        localStorage.setItem(value, value);
        this.todoItems.push(item);
      }
    },
    removeTodo(item, index) {
      localStorage.removeItem(item);
      this.getList();
    },
    getList() {
      this.todoItems = [];
      if (localStorage.length > 0) {
        for (let i = 0; i < localStorage.length; i++) {
          this.todoItems.push(localStorage.key(i));
        }
      }
    },
    clear() {
      this.todoItems = [];
    }
  },

  components: {
    TodoHeader: TodoHeader,
    TodoInput: TodoInput,
    TodoList: TodoList,
    TodoFooter: TodoFooter
  }
};
</script>
