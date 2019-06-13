<template>
  <section id="todo-list">
    <ToDo v-for="todo in todos" :key="todo.id" :todo="todo" />
  </section>
</template>

<script>
  import ToDo from './ToDo';

  export default {
    name: 'ToDoList',
    props: {
      todos: Array
    },
    components: {
      ToDo
    }
  }
</script>

<style>
  #todo-list {
    grid-area: todos;
    display: flex;
    flex-wrap: wrap;
  }
</style>