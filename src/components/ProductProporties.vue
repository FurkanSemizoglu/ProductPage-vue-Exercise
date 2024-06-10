<script setup lang="ts">
import CardTitle from './CardTitle.vue'
import { ref } from 'vue'

import { defineEmits } from 'vue'
import { defineProps } from 'vue'

interface variantsProps {
  id: number
  color: string
  image: string
}

interface Props {
  details: Array<string>
  variants: Array<variantsProps>
  stock: number
}

let selectedVariant = ref<number>(1) // 1 = green, 2 = blue

const props = defineProps<Props>()

console.log('props', props.details)

const emits = defineEmits<{
  (e: 'buttonClicked'): void
  (e: 'selectedImage', image: string): void
}>()

/* const productInfo = ref({
  title: 'Product Title',
  price: 9.99,
  stock: 10,
  inStock: true,
  details: ['50% cotton', '30% wool', '20% polyester'],
  selectedVariant: 0,
  variants: [
    { id: 2234, color: 'green', image: './assets/images/socks_green.jpg' },
    { id: 2235, color: 'blue', image: './assets/images/socks_blue.jpg' }
  ]
}) */

const addToCart = () => {
  console.log('add to cart')
}

console.log('variants', props.variants)

const updateVariant = (id: number) => {
  props.variants.forEach((variant: variantsProps) => {
    if (id === variant.id) {
      console.log('variant', variant)
      selectedVariant.value = id

      emits('selectedImage', variant.color)
    }
  })
}
</script>

<template>
  <div class="product-info">
    <CardTitle />
    <p v-if="stock > 0">In Stock {{ stock }}</p>
    <p v-else>out of Stock</p>

    <ul>
      <li v-for="detail in props.details">{{ detail }}</li>
    </ul>

    <div
      v-for="variant in props.variants"
      :key="variant.id"
      class="color-circle"
      :style="{ backgroundColor: variant.color }"
      @click="updateVariant(variant.id)"
    ></div>
    <button class="button" @click="$emit('buttonClicked')">Add to Cart</button>
  </div>
</template>
