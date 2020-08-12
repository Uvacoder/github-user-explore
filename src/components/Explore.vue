<template>
  <div>
    <input v-model="query" v-on:keyup.enter="search" placeholder="Explore GitHub Repository">

    <div class="row">
      <div class="row-md-6">
        <ul>
          <li v-for="item in items" :key="item.id">
            {{ item.name }}
            <button @click="addStock(item)">Add</button>
          </li>
        </ul>
      </div>
      <div class="row-md-6">
        <ul>
          <li v-for="(stock, index) in stocks" :key="stock.id">
            {{ stock.name }}
            <button @click="removeStock(index)">Remove</button>
          </li>
        </ul>
      </div>
    </div>
  </div>
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
