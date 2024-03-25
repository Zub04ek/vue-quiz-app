<template>
  <div class="text-center py-[100px]">
    <p class="text-[25px]">Your Results...</p>
    <h1 class="text-[80px]">{{ numberOfCorrectAnswers }}/{{ quizQuestionsLength }}</h1>
    <RouterLink to="/">Go Back</RouterLink>
  </div>
</template>

<script setup>
import { defineProps } from 'vue'
import { RouterLink } from 'vue-router'

const { quizQuestionsLength, numberOfCorrectAnswers } = defineProps([
  'quizQuestionsLength',
  'numberOfCorrectAnswers'
])
</script>

<style lang="scss" scoped></style>
