<script setup lang="ts">
import Nav from './components/Nav.vue'
import ImageCard from './components/ImageCard.vue'
import ProductProporties from './components/ProductProporties.vue'
import CardTitle from './components/CardTitle.vue'
import ColorPreference from './components/ColorPreference.vue'
import CardCounter from './components/CardCounter.vue'
import ReviewsContainer from './components/ReviewsContainer.vue'
import AddReview from './components/AddReview.vue'
import { ref } from 'vue'

let productNumber = ref<number>(0)

const details: Array<string> = ['50% cotton', '30% wool', '20% polyester']

interface reviewPost {
  name: string
  review: string
  rating: number
}

const reviews = ref<Array<reviewPost>>([])

const variants = [
  { id: 2234, color: 'green', image: '@/assets/images/socks_green.jpg' },
  { id: 2235, color: 'blue', image: '@/assets/images/socks_blue.jpg' }
]

const stock = ref<number>(5)

const increaseProduct = () => {
  if (stock.value > 0) {
    productNumber.value++
    stock.value--
  }

  console.log(productNumber)
}

let Image = ref<string>('@/assets/images/socks_green.jpg')

let imageType = ref<string>('green')

const selectedImage = (image: string) => {
  console.log('selectedImage', image)
  imageType.value = image
}

const AddReviewHandler = (reviewss: Array<reviewPost>) => {
  reviews.value = reviewss
  console.log('AddReviewHandler', reviewss)
}
</script>

<template>
  <Nav />
  <CardCounter :productNumber="productNumber" />

  <div class="product-display">
    <div class="product-container">
      <ImageCard :imageType="imageType" />
      <!--   <CardTitle /> -->
      <!--  <img :src="imgSrc" :alt="Image" /> -->
      <ProductProporties
        @buttonClicked="increaseProduct"
        :details="details"
        :variants="variants"
        :stock="stock"
        @selectedImage="selectedImage"
      />
    </div>
  </div>

  <ReviewsContainer :reviews="reviews" />
  <AddReview :reviews="reviews" @reviewButtonClicked="AddReviewHandler" />
</template>
