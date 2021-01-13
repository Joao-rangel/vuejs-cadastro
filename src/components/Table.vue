<template>
  <div id="grid-template">
    <table>
      <thead>
        <tr>
          <th v-for="key in columns" :key="key">
            {{ key | capitalize  }}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="entry in filteredClients" :key="entry">
          <td v-for="key in columnKey" :key="key">
            {{entry[key]}}
          </td>
        </tr>
      </tbody>
      <tfoot>
        <tr>
          <td v-for="key in columns" :key="key" style=""></td>
        </tr>
      </tfoot>
    </table>
  </div>
</template>

<script>

export default {
  props: {
        clients: Array,
        columns: Array,
        columnKey: Array,
        filterKey: String
      },
      data: function () {
        var sortOrders = {};
        this.columnKey.forEach(function (key) {
          sortOrders[key] = 1;
        });
        return {
          sortOrders: sortOrders
        };
      },
      computed: {
        filteredClients: function () {
          var filterKey = this.filterKey && this.filterKey.toLowerCase();
          var clients = this.clients;
          if (filterKey) {
            clients = clients.filter(function (row) {
              return Object.keys(row).some(function (key) {
                return (
                  String(row[key])
                    .toLowerCase()
                    .indexOf(filterKey) > -1
                );
              });
            });
          }
          return clients;
        }
      },
            filters: {
        capitalize: function (str) {
          return str.charAt(0).toUpperCase() + str.slice(1);
        }
      },
};
</script>

<style>
table {
  margin-bottom: 320px;
  border-collapse: collapse;
}

th, td {
  border: 2px solid rgba(187, 204, 221, 0.4);
  color: #000;
  width: 180px;
  font-size: 14px;
  font-weight: 700;
  text-align: left;
  padding: 14px 10px;
}

tfoot td {
  height: 640px;
}
</style>