<template>
  <div class="header">
    <form class="header__form" @submit.prevent>
      <input
        class="input"
        :value="title"
        @input="handleInput"
        type="text"
        placeholder="type todo..."
      />
      <button class="btn" @click="addTodo">add</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTodo() {
      if (this.title) {
        this.$emit("addTodo", this.title);
        this.title = "";
      }
    },
    handleInput(e) {
      this.title = e.target.value;
    },
  },
};
</script>

<style>
.header {
  margin: 10px;
}
.header__form {
  margin: 0 auto;
  text-align: center;
}
.input {
  outline: none;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-right: 15px;
}

.btn {
  border: 1px solid teal;
  background-color: #fff;
  cursor: pointer;
  padding: 10px 15px;
}
.btn:hover {
  background-color: teal;
  color: #fff;
}
</style>