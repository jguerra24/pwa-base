<template>
  <section class="todoapp">
    <header>
      <h1>Tareas</h1>
      <input
        type="text"
        class="new-todo"
        autofocus
        autocomplete="off"
        placeholder="Escribe tu tarea pendiente aquí..."
        v-model="newTodo"
        @keyup.enter="addTodo()"
      />
    </header>
    <section class="main" v-show="todos.length">
      <ul>
        <li class="todo-list" v-for="todo in todos" :key="todo.id">
          <input class="toggle" type="checkbox" />
          {{ todo.title }} | {{ todo.completed }}
        </li>
      </ul>
    </section>
  </section>
</template>

<script>
export default {
  data: () => ({
    //todos nuestros datos
    todos: [],
    newTodo: "",
  }),
  methods: {
    //todos los metodos
    addTodo() {
      const value = this.newTodo && this.newTodo.trim();

      const todoItem = {
        id: this.todos.length + 1,
        title: value,
        completed: false,
      };

      if (!value) {
        return;
      }

      this.todos.push(todoItem);
      this.newTodo = "";
    },
  },
};
</script>

<style>
@import "./styles/todomvc-base.css";
@import "./styles/todomvc-index.css";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
