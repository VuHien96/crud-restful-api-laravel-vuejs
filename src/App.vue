<template>
  <div id="app">
    <div class="ui fixed inverted menu vue-color">
      <div class="ui container">
        <a href="#" class="header item">Vue JS CRUD with Laravel API</a>
      </div>
    </div>
    <div class="ui main container">
      <MyForm/>
      <ProductList :products="products"/>
    </div>
  </div>
</template>
<script>
import axios from "axios";
import MyForm from "./components/MyForm";
import ProductList from "./components/ProductList";

export default {
  name: 'App',
  components: {
    MyForm,
    ProductList
  },
  data() {
    return {
      products: []
    }
  },
  methods: {
    getProducts() {
      axios.get("http://localhost:8000/api/products").then(response => {
        this.products = response.data.data;
      })
    }
  },
  created() {
    this.getProducts();
  }
}
</script>
<style>
.vue-color {
  background: #42b983 !important;
}

.vue-color a {
  color: aliceblue;
}

.main.container {
  margin-top: 60px;
}

.submit-button {
  margin-top: 24px !important;
  float: right;
}
</style>
