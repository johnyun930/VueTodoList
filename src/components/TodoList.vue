<style scoped>
li {
  list-style-type: none;
  background-color: antiquewhite;
  width: 250px;
  margin: 5px auto;
  height: 50px;
  padding-top: 20px;
  padding-left: 15px;
  font-weight: bold;
  text-align: left;
}

li span {
  font-size: 20px;
  display: inline-block;
}
</style>

<template>
  <div>
    <section>
      <li v-for="(todoItem, index) in todoItems">
        {{ todoItem }}
        <span v-on:click="removeItem(todoItem, index)">-</span>
      </li>
    </section>
    <button v-on:click="clear">Clear all</button>
  </div>
</template>

<script>
export default {
  props: ["todoItems"],
  methods: {
    removeItem(todoItem) {
      this.$emit("remove-List", todoItem);
    },
    clear() {
      this.$emit("remove-all");
      localStorage.clear();
    }
  }
};
</script>
