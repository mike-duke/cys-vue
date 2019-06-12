<template>
  <article class="todo-card">
    <h3>{{ title }}</h3>
    <hr>
    <div v-for="task in taskList" :key="task.id">
      <input type="checkbox" id="task.id" name="task.title" value="task.title">
      <label for="task.id">{{ task.title }}</label>
    </div>
    <hr>
    <div id="urgent-and-delete-buttons">
      <button>Urgent</button>
      <button>Delete</button>
    </div>
  </article>
</template>

<script>
  export default {
    name: 'ToDo',
    props: {
      todo: {
        type: Object,
        required: false
      }
    },
    data() {
      return {
        title: this.todo.title,
        taskList: this.todo.taskList,
        id: this.todo.id
      }
    },
    methods: {

    }
  }
</script>

<style></style>