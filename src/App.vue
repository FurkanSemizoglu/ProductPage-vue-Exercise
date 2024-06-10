<script setup lang="ts">
import Nav from './components/Nav.vue'
import ImageCard from './components/ImageCard.vue'
import ProductProporties from './components/ProductProporties.vue'
import CardTitle from './components/CardTitle.vue'
import ColorPreference from './components/ColorPreference.vue'
import CardCounter from './components/CardCounter.vue'
import { ref } from 'vue'

let productNumber = ref<number>(0)

const details: Array<string> = ['50% cotton', '30% wool', '20% polyester']

const variants = [
  { id: 2234, color: 'green', image: '../assets/images/socks_green.jpg' },
  { id: 2235, color: 'blue', image: '../assets/images/socks_blue.jpg' }
]

const increaseProduct = () => {
  productNumber.value++
  console.log(productNumber)
}

let Image = ref<string>('../assets/images/socks_green.jpg')
const selectedImage = (image: string) => {
  console.log('selectedImage', image)
  Image.value = image
}
</script>

<template>
  <Nav />
  <CardCounter :productNumber="productNumber" />

  <div class="product-display">
    <div class="product-container">
      <ImageCard :Image="Image" />
      <!--   <CardTitle /> -->

      <ProductProporties
        @buttonClicked="increaseProduct"
        :details="details"
        :variants="variants"
        @selectedImage="selectedImage"
      />

      <ColorPreference />
    </div>
  </div>
</template>
