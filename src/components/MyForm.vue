<template>
  <div class="my-form">
    <form class="ui form">
      <div class="fields">
        <div class="four wide field">
          <label>Name</label>
          <input type="text" name="name" placeholder="Name"/>
        </div>
        <div class="four wide field">
          <label>Price</label>
          <input type="text" name="price" placeholder="price"/>
        </div>
        <div class="six wide field">
          <label>Description</label>
          <input type="text" name="description" placeholder="description"/>
        </div>
        <div class="six wide field">
          <label>Danh muc</label>
          <input type="text" name="category_id" placeholder="category"/>
        </div>
        <div class="two wide field">
          <button class="ui primary button submit-button">
            save
          </button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "MyForm"
}
</script>

<style scoped>

</style>