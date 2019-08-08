<template>
  <div >
    <h3>Lista de Items</h3>
    <ul>
      <li v-for="(item, index) in itemslist" :key="index">{{ item.name }}</li>
    </ul>
  </div>
</template>

<script>
import Axios from 'axios';

const axios = Axios.create({
  baseURL: 'https://domain.com/api/',
  timeout: 1000,
  headers: {'X-Custom-Header': 'foobar'}
});

export default {
  
  name: 'HelloWorld',
  data() {
    return {
      itemslist: []
    }
  },
  methods: {

  },
  mounted() {
    let url = 'http://localhost/laravel-api/mi-api/api/items'
    axios.get(url)
          .then( response => {
            this.itemslist = response.data
          })
  }
}
</script>

<style scoped>

</style>
