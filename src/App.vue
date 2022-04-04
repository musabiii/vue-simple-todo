<template>
  <div id="app">
    <app-header @addTodo="addTodo" />
    <todo-list :todos="todos" @delItem="delItem" @markItem="markItem" />
  </div>
</template>

<script>
import appHeader from "./components/app-header.vue";
import todoList from "./components/todo-list.vue";

export default {
  components: { appHeader, todoList },
  name: "App",
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "some todo",
          completed: false,
        },
      ],
    };
  },
  methods: {
    addTodo(title) {
      const newTodo = {
        id: +new Date(),
        title: title,
        completed: false,
      };
      this.todos.push(newTodo);
    },
    delItem(id) {
      this.todos = this.todos.filter((el) => el.id != id);
    },
    markItem(id) {
      const el = this.todos.find((el) => el.id === id);
      el.completed = !el.completed;
    },
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>
