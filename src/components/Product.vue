<template>
  <tr>
    <td>{{product.id}}</td>
    <td>{{product.name}}</td>
    <td>{{product.description}}</td>
    <td>{{product.price}}</td>
    <td>{{product.status}}</td>
    <td>
      <button class="ui mini blue button">Edit</button>
      <button class="ui mini red button">Delete</button>
    </td>
  </tr>
</template>

<script>
export default {
  name: "Product",
  props: {
    product: {
      type: Object
    }
  }
}
</script>

<style scoped>

</style>
