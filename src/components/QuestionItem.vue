<template>
  <div class="mt-5">
    <h1 class="text-[40px] mb-5">{{ question.text }}</h1>
  </div>
  <ul class="flex flex-col gap-5 cursor-pointer">
    <li
      v-for="option in question.options"
      :key="option.id"
      class="flex items-center"
      @click="emitSelectedOption(option.isCorrect)"
    >
      <p
        class="bg-orange-300 w-[50px] h-[50px] text-[30px] text-black flex items-center justify-center"
      >
        {{ option.label }}
      </p>
      <div class="w-full text-[30px] py-0 px-5">
        <p>{{ option.text }}</p>
      </div>
    </li>
  </ul>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'

const { question } = defineProps(['question'])
const emit = defineEmits(['selectOption'])

const emitSelectedOption = (isCorrect) => {
  emit('selectOption', isCorrect)
}
</script>

<style lang="scss" scoped></style>
