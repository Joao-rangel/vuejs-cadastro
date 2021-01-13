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
        <tr v-for="entry in filteredHeroes" :key="entry">
          <td v-for="key in columns" :key="key">
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
        heroes: Array,
        columns: Array,
        filterKey: String
      },
      data: function () {
        var sortOrders = {};
        this.columns.forEach(function (key) {
          sortOrders[key] = 1;
        });
        return {
          sortOrders: sortOrders
        };
      },
      computed: {
        filteredHeroes: function () {
          var filterKey = this.filterKey && this.filterKey.toLowerCase();
          var heroes = this.heroes;
          if (filterKey) {
            heroes = heroes.filter(function (row) {
              return Object.keys(row).some(function (key) {
                return (
                  String(row[key])
                    .toLowerCase()
                    .indexOf(filterKey) > -1
                );
              });
            });
          }
          // var footerSize = heroes.size();
          return heroes;
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