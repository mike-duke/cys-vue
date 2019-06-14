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
      <button id="urgent-button" @click="updateUrgent">
        <img v-if="urgent" src="../assets/urgent-active.svg" alt="">
        <img v-else src="../assets/urgent.svg" alt="">
        URGENT
      </button>

      <button id="delete-button" @click="deleteToDo">
        <img src="../assets/delete.svg" alt="">
        DELETE
      </button>
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
        id: this.todo.id,
        urgent: this.todo.urgent
      }
    },
    methods: {
      completeTask(e)  {
        const taskId = parseInt(e.target.closest('.task-list-item').dataset.id);
        const todos = this.getToDosFromStorage();
        const todoToUpdate = todos.todos.find((todo) => todo.id === todos.todoId);
        const taskToUpdate = todoToUpdate.taskList.find((task) => task.id === taskId);
        taskToUpdate.completed = !taskToUpdate.completed;
        this.taskList = todoToUpdate.taskList;
        this.setToDosInStorage(todos.todos);
      },
      updateUrgent() {
        const todos = this.getToDosFromStorage();
        const todoToUpdate = todos.todos.find(todo => todo.id === todos.todoId);
        todoToUpdate.urgent = !todoToUpdate.urgent;
        this.urgent = todoToUpdate.urgent;
        this.setToDosInStorage(todos.todos);
      },
      deleteToDo(e) {
        const todos = this.getToDosFromStorage();
        const newTodos = todos.todos.filter(todo => todo.id !== todos.todoId);
        this.setToDosInStorage(newToDos);
        e.target.closest('.todo-card').remove();
      },
      getToDosFromStorage() {
        const todoId = this.$vnode.data.key;
        const todos = JSON.parse(localStorage.getItem('cysToDos'));
        return {todoId, todos};
      },
      setToDosInStorage(todos) {
        localStorage.setItem('cysToDos', JSON.stringify(todos));
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

  #urgent-and-delete-buttons {
    display: flex;
    justify-content: space-between;
    padding: 0 20px;
  }

  .todo-card button {
    all: unset;
    height: 50px;
    width: 50px;
  }
</style>