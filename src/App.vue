<template>
  <div id="app">
    <Aside />
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
      state: {
        todos: []
      }
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
