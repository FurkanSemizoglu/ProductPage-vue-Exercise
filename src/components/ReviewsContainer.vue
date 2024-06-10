<script setup lang="ts">
import { defineProps } from 'vue'

interface Props {
  reviews: Array<any>
}
const props = defineProps<Props>()

console.log('reviseslist', props.reviews)
</script>

<template>
  <div class="review-container">
    <h3>Reviews</h3>

    <ul>
      <li v-for="review in props.reviews">
        {{ review.name }} gave this {{ review.rating }} stars

        <br />
        "{{ review.review }}"
      </li>
    </ul>
  </div>
</template>
