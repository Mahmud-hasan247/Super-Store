<template>
  <div id="app">
    <Navbar @search='search' />
    <div class="container mt-5">
      <div class="row">
      <div class="col-md-9">
        <Inventory @newCartItem='cartItems' :items="items" />
      </div>
      <div class="col-md-3">
        <Cart @removeItem='itemRemove' :items="cart" />
      </div>
    </div>
    </div>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Inventory from './components/Inventory.vue'
import Cart from './components/Cart.vue'
import data from './data.js'

export default {
  name: 'App',
  components: {
    Navbar,
    Inventory,
    Cart
  },
  data() {
    return {
      items: [],
      cart: []
    }
  },
  mounted() {
    this.items = data
  },
  methods: {
    search(keyword) {
      this.items = data.filter(item => {
        return item.name.toLowerCase().indexOf(keyword.toLowerCase()) !== -1
      })
    },
    cartItems(item) {
      this.cart.push(item)
    },
    itemRemove(index) {
      this.cart.splice(index, 1)
    }
  }
}
</script>

<style>
</style>
