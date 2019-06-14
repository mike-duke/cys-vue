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
    data() {
      return {
        todos: []
      }
    },
    created() {
      let storage = JSON.parse(localStorage.getItem('cysToDos'));
      if (storage) {
        this.todos = storage;
      }
    },
    methods: {
      addToDo(todo) {
        this.todos.unshift(todo);
        let storage = JSON.parse(localStorage.getItem('cysToDos'));
        if (storage) {
          localStorage.setItem('cysToDos', JSON.stringify([...this.todos]));
        } else {
          localStorage.setItem('cysToDos', JSON.stringify(this.todos));
        }
      }
    }
  }
</script>

<style>
  * {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 16px; 
    box-sizing: border-box;
  }

  #app {
    display: grid;
    grid-template-areas: 
      "header header"
      "aside todos"
      "aside todos";
    
    grid-template-columns: 30% 1fr;
  }
</style>
