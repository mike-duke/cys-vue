<template>
  <header id="header-component">
    <h1>Check <span id="yo">Yo'</span> Self</h1>
    <form>
      <button id="search-button">
        <img src="../assets/search.svg" alt="Search">
      </button>
      <input type="text" placeholder="Search ToDos" v-model="searchInput" id="search-input" @keyup="searchToDos">
    </form>
  </header>
</template>

<script>
  export default {
    name: 'Header',
    data() {
      return {
        searchInput: ''
      }
    },
    methods: {
      searchToDos(e) {
        this.searchInput = e.target.value;
        this.$emit('search-todos', {
          searchInput: this.searchInput
        });
      }
    }
  }
</script>

<style>
  #header-component {
    grid-area: header;
    background: #1F1F3D;
    display: flex;
    justify-content: space-between;
    height: 10vh;
  }

  header h1 {
    color: #FFFFFF;
    font-weight: 800;
    font-size: 2rem;
  }

  #yo {
    color: #FFC30C;
  }

  #search-button img {
    height: 20px;
    width: 20px;
  }
</style>