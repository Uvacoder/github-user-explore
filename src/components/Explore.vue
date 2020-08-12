<template>
  <div>
    <input v-model="query" v-on:keyup.enter="search" placeholder="Explore GitHub Repository">

    <ul>
      <li v-for="item in items" :key="item.id">
        {{ item.name }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Explore',
  data() {
    return {
      query: '',
      items: []
    }
  },
  methods: {
    search: function() {
      this.items = []
      axios.create({ baseURL: 'https://api.github.com' })
        .get('/search/repositories?q=' + this.query)
        .then(response => (this.items = response.data.items))
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
