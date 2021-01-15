<template>
  <div class="category-list">
    <div class="data">
      <table class="ui celled table">
        <thead>
        <tr>
          <th>ID</th>
          <th>Name</th>
          <th>Description</th>
          <th>Action</th>
        </tr>
        </thead>
        <tbody>
        <Category v-for="category in categories" :key="category.id" :category="category" @onDelete="onDelete"  @onEdit="onEdit"/>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import Category from "./Category";

export default {
  name: "CategoryList",
  components: {
    Category
  },
  props: {
    categories: {
      type: Array
    }
  },
  methods: {
    onDelete(id) {
      this.$emit("onDelete", id);
    },
    onEdit(data) {
      // window.console.log("customer list edit " + data);
      this.$emit("onEdit", data);
    }
  }
}
</script>

<style scoped>

</style>