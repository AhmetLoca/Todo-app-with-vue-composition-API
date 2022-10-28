<template>
  <img class="image" alt="Vue logo" src="./assets/todo1.png" />
  <div class="container">
    <h3 class="title">Todo App</h3>
    <form @submit.prevent>
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
      <button
        @click="addTodo()"
        class="button is-success is-medium is-fullwidth"
      >
        Add
      </button>
      <!-- Cards start -->
      <div v-for="todo in todos" :key="todo.id" class="card my-5">
        <div class="card-content">
          <div class="media">
            <div class="media-content">
              <p class="title is-4" :class="{ done: todo.done }">
                {{ todo.content }}
              </p>
              <button
                @click="
                  {
                    doneTodo(todo);
                  }
                "
                class="button is-danger subtitle is-6"
              >
                {{ todo.done }}
              </button>
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
      //butona bastiktan sonra input alani boşalsin.
      todo.value = "";
    };

    const doneTodo = (todo) => {
      todo.done = !todo.done;
    };

    return {
      todo,
      todos,
      addTodo,
      doneTodo,
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

.done {
  text-decoration: line-through;
}
</style>
