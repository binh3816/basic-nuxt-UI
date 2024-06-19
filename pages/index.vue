<template>
  <div>
    <Header title="Homepage"></Header>
    <v-data-table :custom-filter="filterOnlyCapsText" :headers="headers" :items="products" :search="search"
      item-value="title" show-select>
      <template v-slot:top>
        <v-text-field v-model="search" class="pa-2" label="Search (UPPER CASE ONLY)"></v-text-field>
      </template>
      <template v-slot:[`item.image`]="{ item }">
        <v-img :src="item.image" height="64" cover></v-img>
      </template>
      <template v-slot:[`item.actions`]="{ item }">
        <v-icon small @click="deleteItem(item)">
          mdi-delete
        </v-icon>
      </template>
    </v-data-table>
  </div>
</template>

<script>
import axios from 'axios';
export default {

  data: () => ({
    products: [],
    search: '',
    headers: [
      {
        title: 'Image',
        align: 'start',
        key: 'image',
      },
      {
        title: 'Name',
        align: 'start',
        key: 'title',
      },
      {
        title: 'Price',
        align: 'end',
        key: 'price',
      },
      {
        title: 'Category',
        align: 'end',
        key: 'category',
      },
      { text: 'Actions', value: 'actions', sortable: false },
    ],
  }),

  methods: {
    filterOnlyCapsText(value, query, item) {
      return value != null &&
        query != null &&
        typeof value === 'string' &&
        value.toString().toLocaleUpperCase().indexOf(query) !== -1
    },
    deleteItem(item) {
      // Remove the item from the items array
      this.products = this.products.filter(i => i !== item);
    },
    getProducts() {
      axios
        .get("https://fakestoreapi.com/products")
        .then((response) => {
          this.products = response.data;
          console.log(this.products);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  created() {
    this.getProducts();
  }
}
</script>

<style scoped></style>
