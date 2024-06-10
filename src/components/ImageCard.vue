<script setup lang="ts">
import { defineProps } from 'vue'
import greenSocks from '@/assets/images/socks_green.jpg'
import blueSocks from '@/assets/images/socks_blue.jpg'
interface Props {
  imageType: string
}
const props = defineProps<Props>()
</script>

<template>
  <div class="product-image">
    <img
      v-if="props.imageType === 'green'"
      src="@/assets/images/socks_green.jpg"
      :alt="props.imageType"
    />
    <img v-else src="@/assets/images/socks_blue.jpg" :alt="props.imageType" />
  </div>
</template>
