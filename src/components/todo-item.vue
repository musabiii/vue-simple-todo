<template>
  <div class="todo-item" @click="markItem">
    <input :checked="completed" type="checkbox" />
    <div :class="{ done: completed }">
      {{ title }}
    </div>
    <button @click="delItem" class="btn">delete</button>
  </div>
</template>

<script>
export default {
  props: {
    id: Number,
    title: String,
    completed: Boolean,
  },
  methods: {
    delItem() {
      this.$emit("delItem", this.id);
    },
    markItem() {
      this.$emit("markItem", this.id);
    },
  },
};
</script>

<style scoped>
.todo-item {
  border: 1px solid teal;
  padding: 10px;
  margin: 10px auto;
  max-width: 80%;
  display: flex;
  align-items: center;
  gap: 10px;
}

.btn {
  margin-left: auto;
  text-decoration: none;
}

.done {
  text-decoration: line-through;
}
</style>