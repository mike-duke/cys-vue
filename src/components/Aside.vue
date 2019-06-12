<template>
  <aside>
    <form>
      <label for="title-input">ToDo Title</label>
      <input type="text" id="title-input" :bind="title">
      <section id="new-task-area"></section>
      <label for="item-input">ToDo Task Item</label>
      <input type="text" id="item-input" :bind="task">
      <button id="make-button">Make ToDo</button>
      <button id="clear-button">Clear All</button>
    </form>
    <button id="filter-button">Filter by Urgency</button>
  </aside>
</template>

<script>
  export default {
    name: 'Aside',
    data: {
      title: '',

    }
  }
</script>

<style>

</style>