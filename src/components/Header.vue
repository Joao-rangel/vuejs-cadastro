<template>
  <div class="container">
    <header>
      <nav>
        <router-link to="/clients">
          <i class="fas fa-dot-circle fa-xs" v-if="currentRouteName == 'Lista'"></i>
          Lista
        </router-link>
        <router-link to="/">
          <i class="fas fa-dot-circle fa-xs" v-if="currentRouteName == 'Cadastro'"></i>
          Cadastro
        </router-link>
      </nav>
    </header>
    <div id="title">
      <div>
        <h1>{{currentRouteName}}</h1>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Header',
  computed: {
    currentRouteName() {
      if (this.$route.name === "Clients") return "Lista";
      if (this.$route.name === "ClientForm") return "Cadastro";
      return this.$route.name;
    }
  }
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

  header nav a + a {
    margin-left: 70px;
  }

  header nav a i {
    font-size: 12px;
    position: absolute;
    margin-left: -34px;
    margin-top: 10px;
  }

  #title {
    background: #EFF4F9;
    display: flex;
    justify-content: center;
    margin-bottom: 65px;
  }

  #title div {
    width: 100%;
    max-width: 720px;
    padding: 20px 0;
  }

  #title div h1 {
    font: 80px "Noto Serif", arial, sans-serif;
    font-weight: 400;
  }
</style>
