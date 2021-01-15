<template>
  <tr>
    <td>{{category.id}}</td>
    <td>{{category.name}}</td>
    <td>{{category.description}}</td>
    <td>
      <button class="ui mini blue button" @click="onEdit">Edit</button>
      <button class="ui mini red button" @click="onDelete">Delete</button>
    </td>
  </tr>
</template>

<script>
export default {
name: "Category",
  props: {
    category: {
      type: Object
    }
  },
  methods:{
    onDelete(){
      // window.console.log("Id"+this.product.id);
      this.$emit("onDelete",this.category.id);
    },
    onEdit() {
      // window.console.log("customer edit " + this.category.id);
      this.$emit("onEdit", this.category);
    }
  }
}
</script>

<style scoped>

</style>