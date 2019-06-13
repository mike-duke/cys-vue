<template>
  <header id="header-component">
    <h1>Check <span id="yo">Yo'</span> Self</h1>
    <form>
      <button>Search</button>
      <input type="text" placeholder="search" v-model="searchInput" id="search-input">
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
</style>