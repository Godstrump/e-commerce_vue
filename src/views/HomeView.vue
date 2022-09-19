<template>
  <div class="home">
    <div class="splash-container">
      <div class="splash">
        <h1>Splendid Food</h1>
      </div>
    </div>

    <main class="wrapper">

      <h2>Recommended</h2>

      <div class="recommended">

        <ProductCard :inventory="inventory.slice(0,3)" :addToCart="addProdToCart" />

      </div>

    </main>
  </div>
</template>

<script>

// @ is an alias to /src
import ProductCard from '@/components/ProductCardComponent.vue'

export default {
  name: 'HomeView',
  props: ['inventory', 'addProdToCart'],
  components: {
    ProductCard
  }
}
</script>
