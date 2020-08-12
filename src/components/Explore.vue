<template>
  <v-container>
    <v-text-field v-model="query" v-on:keyup.enter="search" placeholder="Explore GitHub Repository"></v-text-field>

    <v-row>
      <v-col cols="6">
        <v-simple-table>
          <template v-slot:default>
            <thead>
              <tr>
                <th class="text-left">Name</th>
                <th class="text-left"></th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item in items" :key="item.id"> 
                <td>{{ item.name }}</td>
                <td><v-btn x-small @click="addStock(item)">Add</v-btn></td>
              </tr>
            </tbody>
          </template>
        </v-simple-table>
      </v-col>
      <v-col cols="6">
        <v-simple-table>
          <template v-slot:default>
            <thead>
              <tr>
                <th class="text-left">Name</th>
                <th class="text-left"></th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(stock, index) in stocks" :key="stock.id">
                <td>{{ stock.name }}</td>
                <td><v-btn x-small @click="removeStock(index)">Remove</v-btn></td>
              </tr>
            </tbody>
          </template>
        </v-simple-table>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Explore',
  data() {
    return {
      query: '',
      items: [],
      stocks: []
    }
  },
  methods: {
    search: function() {
      this.stocks = []
      this.items = []
      axios.create({ baseURL: 'https://api.github.com' })
        .get('/search/repositories?q=' + this.query)
        .then(response => (this.items = response.data.items))
    },
    addStock: function(item) {
      this.stocks.push(item)
    },
    removeStock: function(index) {
      this.stocks.splice(index, 1)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
