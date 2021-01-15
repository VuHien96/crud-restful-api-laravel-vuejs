<template>
  <div id="app">
    <div class="ui fixed inverted menu vue-color">
      <div class="ui container">
        <a href="#" class="header item">Vue JS CRUD with Laravel API</a>
      </div>
    </div>
    <div class="ui main container">
      <MyForm :form="form" @onFormSubmit="onFormSubmit"/>
      <Loader v-if="loader"/>
      <CategoryList :categories="categories" @onDelete="onDelete" @onEdit="onEdit"/>
    </div>
  </div>
</template>
<script>
import axios from "axios";
import Loader from "./components/Loader";

import MyForm from "./components/MyForm";
import CategoryList from "./components/CategoryList";

export default {
  name: 'App',
  components: {
    MyForm,
    CategoryList,
    Loader
  },
  data() {
    return {
      url: "http://localhost:8000/api/categories",
      categories: [],
      form: {name: "", description: "", isEdit: false},
      loader: false
    }
  }
  , methods: {
    getCategories() {
      this.loader = true;
      axios.get(this.url).then(response => {
        this.categories = response.data.data;
        this.loader = false;
      })
    },
    createCategory(data) {
      this.loader = true;
      axios.post(this.url, {
        name: data.name,
        description: data.description,
      })
          .then(() => {
            this.getCategories();
          })
          .catch(e => {
            alert(e);
          });
    },
    editCategory(data) {
      this.loader = true;
      axios
          .put(`${this.url}/${data.id}`, {
            name: data.name,
            description: data.description,
          })
          .then(() => {
            this.getCategories();
          })
          .catch(e => {
            alert(e);
          });
    },
    deleteCategory(id) {
      this.loader = true;
      axios.delete(`${this.url}/${id}`).then(() => {
        this.getCategories();
      }).catch(e => {
        alert(e);
      });
    },
    onDelete(id) {
      this.deleteCategory(id);
    },
    onEdit(data) {
      // window.console.log("app edit ", data);
      this.form = data;
      this.form.isEdit = true;
    },
    onFormSubmit(response) {
      // window.console.log("Data",response);
      if (response.isEdit) {
        // call edit category
        this.editCategory(response);
      } else {
        // call create category
        this.createCategory(response);
      }
    }
  }
  , created() {
    this.getCategories();
  }
}
</script>
<style>
.vue-color {
  background: #41b883 !important;
}

.main.container {
  margin-top: 60px;
}

.submit-button {
  margin-top: 24px !important;
  float: right;
}

.data {
  margin-top: 15px;
}

thead tr th {
  background: #e0e0e0 !important;
}

.ui.inverted.dimmer {
  background-color: rgba(255, 255, 255, 0) !important;
}

</style>
