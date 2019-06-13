<template>
  <div id="app">
    <Header />
    <Aside @make-todo="addToDo" />
    <ToDoList :todos="todos" />
  </div>
</template>

<script>
import Header from './components/Header';
import Aside from './components/Aside';
import ToDoList from './components/ToDoList';
import './assets/reset.css';

export default {
  name: 'app',
  components: {
    Header,
    Aside,
    ToDoList,
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

</style>
