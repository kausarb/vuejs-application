<script>
import beers from "./components/json/beers.json";
import moment from "moment";

export default {
  data() {
    return {
      beer: beers,
    };
  },
  methods: {
    momentDateFormat(val) {
      return moment(val).format("DD/MM/YY");
    },
  },
};
</script>

<template>
  <div>
    <table id="beer-table">
      <tr>
        <th>Brewery ID</th>
        <th>Name</th>
        <th>Description</th>
        <th>Last Modified</th>
      </tr>
      <tr v-for="beer in beer.data" v-bind:key="beer.id">
        <td>{{ beer.brewery_id }}</td>
        <td>{{ beer.name }}</td>
        <td>{{ beer.descript }}</td>
        <td>{{ momentDateFormat(beer.last_mod) }}</td>
      </tr>
    </table>
  </div>
</template>

<style>
@import "@/assets/base.css";

#beer-table {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

#beer-table td,
#beer-table th {
  border: 1px solid #ddd;
  padding: 30px;
}

#beer-table tr:nth-child(even) {
  background-color: #f2f2f2;
}

#beer-table tr:hover {
  background-color: #ddd;
}

#beer-table th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: center;
  background-color: #800080;
  color: white;
}

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }
}
</style>
