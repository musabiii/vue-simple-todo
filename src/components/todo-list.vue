<template>
  <div class="div">
    <div v-if="!todos.length" class="empty-list">List is empty</div>
    <div class="todo-list">
      <todo-item
        :id="todo.id"
        :title="todo.title"
        :completed="todo.completed"
        v-for="todo in todos"
        :key="todo.id"
        @delItem="delItem"
        @markItem="markItem"
      />
    </div>
  </div>
</template>

<script>
import todoItem from "./todo-item.vue";

export default {
  components: { todoItem },
  props: {
    todos: {
      type: Array,
      required: true,
    },
  },
  methods: {
    delItem(id) {
      this.$emit("delItem", id);
    },
    markItem(id) {
      this.$emit("markItem", id);
    },
  },
};
</script>

<style scoped>
.todo-list {
  margin: 15px;
}

.empty-list {
  text-align: center;
  color: gray;
    font-weight: 600;
}
</style>