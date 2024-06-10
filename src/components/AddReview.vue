<script setup lang="ts">
import { defineProps, ref, defineEmits } from 'vue'

interface Props {
  reviews: Array<any>
}

const emits = defineEmits<{
  (e: 'reviewButtonClicked', reviews: Array<any>): void
}>()

const props = defineProps<Props>()

console.log(props.reviews)

const inputName = ref('')
const inputReview = ref('')
const inputRating = ref(0)

const formSubmit = () => {
  console.log('form submitted', inputName.value)

  const review = {
    name: inputName.value,
    review: inputReview.value,
    rating: inputRating.value
  }

  props.reviews.push(review)

  emits('reviewButtonClicked', props.reviews)
}
</script>

<template>
  <form class="review-form" @submit.prevent="formSubmit">
    <h3>Leave a review</h3>

    <label for="name"> Name:</label>
    <input type="text" id="name" v-model="inputName" />

    <label for="review">Review:</label>
    <textarea id="review" v-model="inputReview"></textarea>

    <label for="rating">Rating:</label>

    <select id="rating" v-model="inputRating">
      <option value="1">1</option>
      <option value="2">2</option>
      <option value="3">3</option>
      <option value="4">4</option>
      <option value="5">5</option>
    </select>
    <button class="button">Submit</button>
    <!--    <input type="submit" class="button" /> -->
  </form>
</template>
