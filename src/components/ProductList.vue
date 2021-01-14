<template>
  <div class="product-list">
    <div class="data">
      <table class="ui celled table">
        <thead>
        <tr>
          <th>ID</th>
          <th>Name</th>
          <th>Description</th>
          <th>Price</th>
          <th>Status</th>
          <th>Action</th>
        </tr>
        </thead>
        <tbody>
        <Product v-for="product in products" :key="product.id" :product="product"/>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import Product from "./Product";

export default {
  name: "ProductList",
  components: {
    Product
  },
  props:{
    products:{
      type:Array
    }
  }
}
</script>

<style scoped>

</style>