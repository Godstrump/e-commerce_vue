<template>
  <header class="top-bar spread">
    <nav class="top-bar-nav">
      <router-link to="/" class="top-bar-link">
        <i class="icofont-spoon-and-fork"></i>
        <span>Home</span>
      </router-link>
      <router-link to="/products" class="top-bar-link">
        <span>Products</span>
      </router-link>
      <router-link to="/past-orders" class="top-bar-link">
        <span>Past Orders</span>
      </router-link>
    </nav>
    <div @click="toggleSideBar" class="top-bar-cart-link">
      <i class="icofont-cart-alt icofont-1x"></i>
      <span>Cart ({{ totalQuantity }})</span>
    </div>
  </header>
  <router-view :inventory="inventory" :addProdToCart="addToCart" />

  <SidebarComponent v-if="showSideBar" T :toggle="toggleSideBar" :cart="cart" :inventory="inventory"
    :remove="removeItem" />
</template>

<!-- <style scoped>

</style> -->
<script>
import SidebarComponent from '@/components/SidebarComponent.vue'
import food from './food.json'

export default {
  components: {
    SidebarComponent
  },
  data () {
    return {
      showSideBar: false,
      inventory: food,
      cart: {}
    }
  },
  computed: {
    totalQuantity () {
      return Object.values(this.cart).reduce((acc, curr) => (acc + curr), 0)
    }
  },
  methods: {
    addToCart (name, index) {
      if (!this.cart[name]) this.cart[name] = 0
      // receive name and number
      this.cart[name] += this.inventory[index].quantity
      console.log(this.cart)
      this.inventory[index].quantity = 0
    },
    toggleSideBar () {
      this.showSideBar = !this.showSideBar
    },
    removeItem (name) {
      delete this.cart[name]
    }
  }
}
</script>
