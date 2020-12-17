<template>
  <div class="list_container">
    <ul v-for="item in items" :key="item.id" class="list">
      <li class="list_item" :class="item.completed ? 'isCompleted' : null">
        {{ item.text }}
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="15"
          height="15"
          fill="currentColor"
          class="bi bi-trash-fill deleteIcon"
          viewBox="0 0 16 16"
          @click="$emit('deleteTodo', item)"
        >
          <path
            fill-rule="evenodd"
            d="M2.5 1a1 1 0 0 0-1 1v1a1 1 0 0 0 1 1H3v9a2 2 0 0 0 2 2h6a2 2 0 0 0 2-2V4h.5a1 1 0 0 0 1-1V2a1 1 0 0 0-1-1H10a1 1 0 0 0-1-1H7a1 1 0 0 0-1 1H2.5zm3 4a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7a.5.5 0 0 1 .5-.5zM8 5a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7A.5.5 0 0 1 8 5zm3 .5a.5.5 0 0 0-1 0v7a.5.5 0 0 0 1 0v-7z"
          />
        </svg>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="15"
          height="15"
          fill="currentColor"
          class="bi bi-pen-fill editIcon"
          viewBox="0 0 16 16"
          @click="$emit('toggleComplete', item)"
        >
          <path
            fill-rule="evenodd"
            d="M13.498.795l.149-.149a1.207 1.207 0 1 1 1.707 1.708l-.149.148a1.5 1.5 0 0 1-.059 2.059L4.854 14.854a.5.5 0 0 1-.233.131l-4 1a.5.5 0 0 1-.606-.606l1-4a.5.5 0 0 1 .131-.232l9.642-9.642a.5.5 0 0 0-.642.056L6.854 4.854a.5.5 0 1 1-.708-.708L9.44.854A1.5 1.5 0 0 1 11.5.796a1.5 1.5 0 0 1 1.998-.001z"
          />
        </svg>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["items"],
  emits: ["deleteTodo", "toggleComplete"],
  methods: {},
};
</script>

<style>
.list {
  list-style-type: none;
}
.list_container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;
}
li {
  width: 50%;
  background: #dce1e3;
  color: #2c3e50;
  padding: 0.2rem;
  margin: 0 auto;
  border: 1px solid transparent;
  border-radius: 5%;
}
.isCompleted {
  text-decoration: line-through;
  opacity: 0.6;
}
.deleteIcon {
  margin: 0 0.5rem;
}
.deleteIcon,
.editIcon {
  cursor: pointer;
}
</style>