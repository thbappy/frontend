<template>
  <div class="product">
    <div class="container">
      <h3>Product List</h3>
      <table class="table table-striped">
        <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Title</th>
          <th scope="col">Image</th>
          <th scope="col">Price</th>
          <th scope="col">Description</th>
        </tr>
        </thead>
        <tbody v-for="(value,index) in infos" :key="index">
        <tr>
          <th scope="row">{{ ++index }}</th>
          <td>{{ value.title }}</td>
          <td><img :src="(value.image)" alt="" style="width:50px;height: 50px"></td>
          <td>{{ value.price }}</td>
          <td>{{ value.description }}</td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'ProductList',
  data () {
    return {
      infos: null
    }
  },
  mounted () {
    axios
      .get('http://127.0.0.1:8000/api/product/all')
      .then(response => (this.infos = response.data.data))
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
