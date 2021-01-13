<template>
  <div id="app">
    <Header/>
    <main>
      <router-view />
    </main>
    <Footer/>
  </div>
</template>

<script>
import Header from './components/Header';
import Footer from './components/Footer';

export default {
  components: {
    Header,
    Footer
  }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    outline: 0;
    box-sizing: border-box;
  }

  #app {
    display: flex;
    min-height: 100vh;
    flex-direction: column;
  }

  main {
    flex: 1;
    display: flex;
    justify-content: center;
  }

  body, input, button {
    font: 18px Nunito, arial, sans-serif;
    color: #445566;
    -webkit-font-smoothing: antialiased
  }

  button {
    cursor: pointer;
  }
</style>
