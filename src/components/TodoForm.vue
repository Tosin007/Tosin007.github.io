<template>
  <div>
    <header>
      <h2 v-if="items.length">
        You have {{ items.length }}
        plan(s) today
      </h2>
      <h2 v-else>What Are Your Plans For Today?</h2>
    </header>

    <form @submit.prevent="emitTodo">
      <input type="text" placeholder="Enter Todo" v-model="todo" />
      <button>Enter</button>
      <button @click="$emit('clearAllTodo')">Delete All</button>
    </form>
  </div>
</template>

<script>
export default {
  emits: ["childToParent", "clearAllTodo"],
  props: ["items"],
  components: {},
  data() {
    return {
      todo: "",
    };
  },
  methods: {
    emitTodo() {
      if (this.todo.trim().length !== 0) {
        this.$emit("childToParent", this.todo);
        this.todo = "";
      }
    },
  },
};
</script>

<style>
</style>