<template>
  <tr>
    <td>{{product.id}}</td>
    <td>{{product.name}}</td>
    <td>{{product.description}}</td>
    <td>{{product.price}}</td>
    <td>{{product.status}}</td>
    <td>
      <button class="ui mini blue button">Edit</button>
      <button class="ui mini red button" @click="onDelete">Delete</button>
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
  },
  methods:{
    onDelete(){
      // window.console.log("Id"+this.product.id);
      this.$emit("onDelete",this.product.id);
    }
  }
}
</script>

<style scoped>

</style>
