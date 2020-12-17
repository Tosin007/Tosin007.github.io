<template>
  <div class="container">
    <h1>My Todo App</h1>
    <todo-form
      :items="items"
      @childToParent="createNewTodo($event)"
      @clearAllTodo="clearAllTodo"
    />
    <todolist
      :items="items"
      @deleteTodo="removeTodo($event)"
      @toggleComplete="toggleComplete($event)"
    />
  </div>
</template>

<script>
import TodoForm from "./components/TodoForm.vue";
import Todolist from "./components/Todolist.vue";
export default {
  name: "App",
  components: { TodoForm, Todolist },
  data() {
    return {
      items: [
        {
          id: 1,
          text: "Go to school",
          completed: false,
        },
        {
          id: 2,
          text: "Walk The Dog",
          completed: false,
        },
        {
          id: 3,
          text: "Do the Laundry",
          completed: true,
        },
      ],
    };
  },
  methods: {
    createNewTodo(value) {
      this.items.push({
        id: Math.floor(Math.random() * 100),
        text: value,
        completed: false,
      });
    },
    clearAllTodo() {
      this.items = "";
    },
    removeTodo(value) {
      this.items = this.items.filter((item) => item.id !== value.id);
    },
    toggleComplete(value) {
      value.completed = !value.completed;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  margin: 0;
  background: #eee;
}
.container {
  background: #283747;
  max-width: 960px;
  height: 100vh;
  margin: 2rem auto;
  color: #eee;
  padding: 1rem;
  display: flex;
  flex-direction: column;
}
button {
  background: #b73225;
  color: white;
  margin: 0 0.1rem;
  padding: 0.2rem;
  cursor: pointer;
}
button:active,
button:focus,
input {
  outline: none;
}
</style>
