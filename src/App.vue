<template>
  <div class="container">
    <div class="row">
      <div class="col-md-7">
        <div class="row">
          <div :key="product.id" class="col-md-6" v-for="product in products">
            <Product v-on:add-to-cart="addToCart(product)" :product="product" :isInCart="isInCart(product)"></Product>
          </div>
        </div>
      </div>
      <div class="col-md-5 my-5">
        <Cart :items="cart" v-on:remove-from-cart="removeFromCart($event)" v-on:pay="pay()"></Cart>
      </div>
    </div>
  </div>
</template>

<script>

import products from '@/products.json';
// Import Product Component

import Product from '@/components/Product.vue';

// Import Cart component
import Cart from '@/components/Cart.vue'

export default {
  name: 'app',

  components: {
    Product,
    Cart
  },

  data() {
  return {
    products,
    cart: []
  }
},
methods: {
  addToCart(product) {
    this.cart.push(product);
  },
  isInCart(product) {
    const item = this.cart.find(item => item.id === product.id);
    if(item) {
      return true;
    }
    return false;
  },
  removeFromCart(product) {
    this.cart = this.cart.filter(item => item.id !== product.id);
  },
  pay() {
    alert('Shopping Completed')
    this.cart = []
  }
}

}

</script>

<style>
  body {
    background-color: #FBF8F3;
  }
</style>
