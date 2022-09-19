<template>
  <main class="wrapper">
    <h1>Products</h1>

    <div class="card-container">
      <ProductCard :inventory="inventory" :addToCart="addProdToCart" />
    </div>
  </main>
</template>

<script>
import ProductCard from '@/components/ProductCardComponent.vue'

export default {
  props: ['inventory', 'addProdToCart'],
  components: {
    ProductCard
  }
}
</script>
