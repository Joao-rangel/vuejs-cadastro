<template>
  <div id="container">
    <h2>Lista de Clientes</h2>
    <hr>

    <form id="search">
      <label for="name">Nome do Cliente</label>
      <input type="text" name="query" v-model="searchQuery">
    </form>

    <Table :heroes="gridData" :columns="gridColumns" :filter-key="searchQuery" />
  </div>
</template>

<script>
import Table from '../components/Table';

export default {
  name: 'Clients',
  components: {
    Table
  },
  data: function() {
    return {
      searchQuery: "",
      gridColumns: ["nome", "email", "cpf", "criado em"],
      gridData: [
        { nome: "Chuck Norris", email: "teste12@teste.com", cpf: Infinity, "criado em": "12/01/2021" },
        { nome: "Bruce Lee", email: "teste23@teste.com", cpf: 9000, "criado em": "12/01/2021" },
        { nome: "Jackie Chan", email: "teste44@teste.com", cpf: 7000, "criado em": "12/01/2021" },
        { nome: "Jet Li", email: "teste45@teste.com", cpf: 8000, "criado em": "12/01/2021" }
      ]
    }
  }
}
</script>

<style scoped>
#container {
  width: 100%;
  max-width: 720px;
}

h2 {
  color: #1188EE;
  font-size: 24px;
}

label {
  font-size: 23px;
  font-weight: 700;
}

hr {
  border: 1.2px solid #EFF4F9;
  background: #EFF4F9;
  margin: 16px 0 32px 0;
}

input {
  width: 100%;
  height: 62px;
  margin: 4px 0 60px 0;
  padding-left: 16px;
  border-radius: 5px;
  border: 0;
  background: #EFF4F9;
  box-shadow: 0px 2px 2px rgba(187, 204, 221, 0.4);
}

input:focus, select:focus {
  border: 2px solid #17222D;
}
</style>
