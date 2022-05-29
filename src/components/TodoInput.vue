<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}

.addContainer {
  background: linear-gradient(to right, #6478fb, #8763fb);
  display: inline-block;
  font-size: large;
  font-weight: bold;
  color: white;
  width: 3em;
  border-radius: 0 5px 5px 0;
}

.addBtn {
  color: white;
  vertical-align: middle;
}
</style>

<template>
  <div class="inputBox shadow">
    <input
      type="text"
      v-model="newTodoItem"
      placeholder="Type what you have to do"
      v-on:keyup.enter="addList(newTodoItem)"
    />
    <span class="addContainer" v-on:click="addList(newTodoItem)">
      +
    </span>
  </div>
</template>
<script>
export default {
  data() {
    return {
      newTodoItem: ""
    };
  },
  methods: {
    addList(item) {
      if (item === "") return;
      this.$emit("add-List", item);
      this.clearInput();
    },
    clearInput() {
      this.newTodoItem = "";
    }
  }
};
</script>
