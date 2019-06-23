<template>
  <aside id="aside-component">
    <form>
      <label for="title-input">ToDo Title</label>
      <input type="text" id="title-input" v-model="titleInput" ref="titleInput">
      <ul id="task-list">
        <li v-for="task in tasks" :key="task.id">
          {{ task.title }}
        </li>
      </ul>
      <label for="item-input">ToDo Task Item</label>
      <input type="text" id="item-input" v-model="taskInput" ref="itemInput">
      <button id="add-task-button" @click.prevent="addTask">+</button>
      <button id="make-button" @click.prevent="makeToDo">Make ToDo</button>
      <button id="clear-button" @click.prevent="clearForm">Clear All</button>
    </form>
    <hr>
    <button id="filter-button" @click="filterToDos">Filter by Urgency</button>
  </aside>
</template>

<script>
  export default {
    name: 'Aside',
    data: () => {
      return {
        titleInput: '',
        taskInput: '',
        tasks: []
      }
    },
    mounted() {
      this.$refs.titleInput.focus();
    },
    methods: {
      addTask() {
        this.tasks.push({
          title: this.taskInput, 
          completed: false,
          id: Date.now()
          });
        this.taskInput = '';
        this.$refs.itemInput.focus();
      },
      makeToDo() {
        this.$emit('make-todo', {
          title: this.titleInput, 
          tasks: this.tasks, 
          id: Date.now(),
          urgent: false
        });
        this.clearForm();
      },
      clearForm() {
        this.titleInput = '';
        this.taskInput = '';
        this.tasks = [];
      },
      filterToDos(e) {
        this.$emit('filter-todos', {
          classList: e.target.classList
        });
      }
    }
  }
</script>

<style>
  #aside-component {
    grid-area: aside;
    background: #587A8A;
    min-height: 90vh;
  }
</style>