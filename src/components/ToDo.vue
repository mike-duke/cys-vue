<template>
  <article class="todo-card">
    <h3>{{ title }}</h3>
    <hr>
    <ul>
      <li v-for="task in taskList" :key="task.id" :data-id="task.id" @click="completeTask" class="task-list-item">
        <img v-if="!task.completed" src="../assets/checkbox.svg" class="checkbox" alt="">
        <img v-else src="../assets/checkbox-active.svg" class="checkbox" alt="">
        <span class="task-title" :class="{ completedTask: task.completed }">{{ task.title }}</span>
      </li>
    </ul>
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
      completeTask(e) {
        const taskKey = parseInt(e.target.closest('.task-list-item').dataset.id);
        const taskToUpdate = this.taskList.find((task) => task.id === taskKey);
        taskToUpdate.completed = !taskToUpdate.completed;
      }
    }
  }
</script>

<style>
  .todo-card {
    width: 40%;
    height: 400px;
    margin: 20px;
  }

  .todo-card:nth-child(odd) {
    background: #FFE89D;
    border: 2px solid #FFC30C;
  }

  .todo-card:nth-child(even) {
    background: #FAFDFF;
    border: 2px solid #C7D3D8;
  }

  .checkbox {
    height: 50px;
    width: 50px;
  }

  .completedTask {
    font-style: italic;
    color: gray;
  }
</style>