<template>
  <div id="app">
    <Aside @make-todo="addToDo" />
    <ToDoList :todos="todos" />
  </div>
</template>

<script>
import Aside from './components/Aside.vue';
import ToDoList from './components/ToDoList';

export default {
  name: 'app',
  components: {
    Aside,
    ToDoList
  },
  data: () => {
    return {
      todos: []
    }
  },
  methods: {
    addToDo(todo) {
      this.todos.push(todo);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
