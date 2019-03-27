<template>
  <div id="app">
    <h1 class="ui dividing centered header">Vue.js App 1</h1>
    <div class='ui three column centered grid'>
      <div class='column'>
        <products-list v-bind:products="products"></products-list>
        <create-product v-on:create-product="createProduct"></create-product>
      </div>
    </div>
  </div>
</template>

<script>
import sweetalert from 'sweetalert';
import ProductsList from './components/ProductsList';
import CreateProduct from './components/CreateProduct';

export default {
  name: 'app',
  components: {
    ProductsList,
    CreateProduct,
  },
  data() {
    return {
      products: [{
        name: 'product A',
        description: 'Abc'
      }, {
        name: 'product b',
        description: 'Cdn'
      }, ],
    };
  },
  methods: {
    createProduct(newProduct) {
      this.products.push(newProduct);
      sweetalert('Success!', 'Product created!', 'success');
    },
  },
};
</script>