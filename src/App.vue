<template>
  <div id="app">
    <Aside @make-todo="addToDo" />
  </div>
</template>

<script>
import Aside from './components/Aside.vue'

export default {
  name: 'app',
  components: {
    Aside
  },
  data: () => {
    return {
      todos: []
    }
  },
  methods: {
    addToDo(todo) {
      this.todos.push(todo);
      console.log(this.todos);
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
