<template>
  <div id="app">
    <Header/>
    <router-view />
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

  body {
    background: #EFF4F9 ;
  }

  body, input, button {
    font: 16px Nunito, sans-serif;
    -webkit-font-smoothing: antialiased
  }

  button {
    cursor: pointer;
  }
</style>
