<template>
  <div id="container">
    <h2>Lista de Clientes</h2>
    <hr>

    <form id="search">
      <label for="name">Nome do Cliente</label>
      <input type="text" name="query" v-model="searchQuery">
    </form>

    <Table :clients="gridData" :columns="gridColumns" :column-key="gridColumnKeys" :filter-key="searchQuery" />
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
      gridColumnKeys: ["name", "email", "cpf", "created-at"],
      gridColumns: ["nome", "email", "cpf", "criado em"],
      gridData: []
    }
  },
  methods: {
    getClients() {
      fetch("http://localhost:3333/client")
        .then(response => response.json())
        .then(response => {
          this.gridData = response;
        });
    }
  },
  created() {
    this.getClients();
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
