<template>
  <div id="app">
    <Header @search-todos="search" />
    <Aside @make-todo="addToDo" @filter-todos="filterByUrgent" />
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
      },
      filterByUrgent(el) {
        let { classList } = el;
        if (classList.contains('clicked')) {
          classList.remove('clicked');
          this.todos = JSON.parse(localStorage.getItem('cysToDos'));
        } else {
          classList.add('clicked')
          this.todos = this.todos.filter(todo => {
            return todo.urgent === true
          });
        }
      },
      search(e) {
        if (!e.searchInput) {
          this.todos = JSON.parse(localStorage.getItem('cysToDos'));
        }
        this.todos = this.todos.filter(todo => {
          const taskArray = todo.tasks.filter(task => {
            return task.title.includes(e.searchInput);
          });
          return todo.title.includes(e.searchInput) || taskArray.length !== 0;
        });
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
