<template>
  <img class="image" alt="Vue logo" src="./assets/todo1.png" />
  <div class="container">
    <h3 class="title">Todo App</h3>
    <form @submit.prevent="addTodo()">
      <!-- input start -->
      <div class="field">
        <div class="control">
          <input
            v-model="todo"
            class="input"
            type="text"
            placeholder="Add a new task"
          />
        </div>
      </div>
      <!-- input finish -->
      <button class="button is-success is-medium is-fullwidth">Add</button>
      <!-- Cards start -->
      <div v-for="todo in todos" :key="todo.id" class="card my-5">
        <div class="card-content">
          <div class="media">
            <div class="media-content">
              <p class="title is-4">{{ todo.content }}</p>
              <p class="subtitle is-6">{{ todo.done }}</p>
            </div>
          </div>
        </div>
      </div>
      <!-- Cards finish -->
    </form>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const todo = ref("");
    const todos = ref([]);

    const addTodo = () => {
      todos.value.push({
        content: todo.value,
        done: false,
        id: Date.now(),
      });
    };

    return {
      todo,
      todos,
      addTodo,
    };
  },
};
</script>

<style>
.container {
  padding: 20px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}
.image {
  height: 300px;
  display: block;
  margin-left: auto;
  margin-right: auto;
}
</style>
