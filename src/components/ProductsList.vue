<template>
  <div>
    <p class="prods">Products so far: {{products.length}}</p>
    <!-- <div v-for="product in products">{{product.name}}</div> -->
    <product v-for="product in products"  v-bind:product="product"></product>
  </div>
</template>
<script type = "text/javascript" >
import sweetalert from 'sweetalert';
import Product from './Product';

export default {
  props: ['products'],
  components: {
    Product,
  },
  created: async ()=>{
      const products = await fetch("http://localhost:8080/api/products");
      this.products = products;
  }
};
</script>

<style scoped>
p.prods {
  text-align: center;
}
</style>
