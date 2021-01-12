<template>
  <header>
    <nav>
      <router-link to="/">
        Lista
      </router-link>
      <router-link to="Clients">
        <i class="fas fa-dot-circle fa-xs"></i>
        Cadastro
      </router-link>
    </nav>
    <div id="title">
      <div>
        <h1>Cadastro</h1>
      </div>
    </div>
  </header>
</template>

<script>
  export default {
    name: 'Header',
  }
</script>

<style scoped>
  header {
    width: 100%;
    background: #17222D;
  }

  header nav {
    display: flex;
    justify-content: flex-end;
    padding: 22px 70px;
  }

  header nav a {
    color: #FFFFFF;
    font-size: 22px;
    font-weight: 700;
    text-decoration: none;
  }

  header nav a i {
    font-size: 12px;
    margin: 0 16px 2px 54px;
    vertical-align: middle;
  }

  #title {
    background: #EFF4F9;
    display: flex;
    justify-content: center;
  }

  #title div {
    width: 100%;
    max-width: 720px;
    padding: 20px 0;
  }

  #title h1 {
    font: 80px "Noto Serif", arial, sans-serif;
    font-weight: 400;
  }
</style>
