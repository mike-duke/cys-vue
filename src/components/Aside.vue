<template>
  <aside id="aside-component">
    <form>
      <label for="title-input">ToDo Title</label>
      <input type="text" id="title-input" v-model="titleInput">
      <ul id="task-list">
        <li v-for="task in taskList" :key="task.id">
          {{ task.title }}
        </li>
      </ul>
      <label for="item-input">ToDo Task Item</label>
      <input type="text" id="item-input" v-model="taskInput">
      <button id="add-task-button" @click.prevent="addTask">+</button>
      <button id="make-button" @click.prevent="makeToDo">Make ToDo</button>
      <button id="clear-button" @click.prevent="clearForm">Clear All</button>
    </form>
    <hr>
    <button id="filter-button">Filter by Urgency</button>
  </aside>
</template>

<script>
  export default {
    name: 'Aside',
    data: () => {
      return {
        titleInput: '',
        taskInput: '',
        taskList: []
      }
    },
    methods: {
      addTask() {
        this.taskList.push({title: this.taskInput, id: Date.now()});
        this.taskInput = '';
      },
      makeToDo() {
        this.$emit('make-todo', {title: this.titleInput, taskList: this.taskList, id: Date.now()});
        this.clearForm();
      },
      clearForm() {
        this.titleInput = '';
        this.taskInput = '';
        this.taskList = [];
      }
    }
  }
</script>

<style>
  #aside-component {
    grid-area: aside;
    background: #587A8A;
    height: 90vh;
  }
</style>