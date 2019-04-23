<template>
  <div class="todo-item">
    <p>
      <input type="checkbox" v-model="todo.completed" v-on:change="markComplete">
      <span :class="{'is-complete':todo.completed}">{{ todo.title }}</span>
      <button class="del" @click="$emit('del-todo', todo.id)">&times;</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  },
}
</script>

<style scoped>
  .todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px dotted #ccc;
  }
  .is-complete {
    text-decoration: line-through;
  }
  input[type="checkbox"] {
    margin-right: 5px;
  }
  .del {
    background: #f00;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>
