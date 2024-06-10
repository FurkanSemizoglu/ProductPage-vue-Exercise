<script setup lang="ts">
import { defineProps } from 'vue'

interface Props {
  productNumber: number
}
const props = defineProps<Props>()

console.log('props', props.productNumber)
</script>

<template>
  <div class="cart">Card({{ props.productNumber }})</div>
</template>
