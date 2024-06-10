<script setup lang="ts">
import Nav from './components/Nav.vue'
import ImageCard from './components/ImageCard.vue'
import ProductProporties from './components/ProductProporties.vue'
import CardTitle from './components/CardTitle.vue'
import ColorPreference from './components/ColorPreference.vue'
import CardCounter from './components/CardCounter.vue'
</script>

<template>
  <Nav />
  <CardCounter />

  <div class="product-display">
    <div class="product-container">
      <ImageCard />
      <!--   <CardTitle /> -->

      <ProductProporties />

      <ColorPreference />
    </div>
  </div>
</template>
