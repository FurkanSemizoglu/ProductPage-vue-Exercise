<script setup lang="ts">
import { defineProps } from 'vue'

interface Props {
  Image: string
}
const props = defineProps<Props>()

let newUrl: string = '".' + props.Image + '"'

console.log('0newUrl', newUrl)

console.log('propsImage', props.Image)
</script>

<template>
  <div class="product-image">
    <img :src="props.Image" :alt="props.Image" />
  </div>
</template>
