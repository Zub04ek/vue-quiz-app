<template>
  <li
    class="w-[310px] overflow-hidden rounded-[2%] shadow-[1px_1px_10px_rgba(0,0,0,0.1)] cursor-pointer"
    @click="navigateToQuiz"
  >
    <img :src="item.img" :alt="item.name" class="w-full h-[190px] m-0" />
    <div class="py-0 px-[5px]">
      <h2 class="font-bold">{{ item.name }}</h2>
      <p>{{ item.questions.length }} questions</p>
    </div>
  </li>
</template>

<script setup>
import { defineProps } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const { item } = defineProps(['item'])

const navigateToQuiz = () => {
  router.push(`/quiz/${item.id}`)
}
</script>

<style lang="scss" scoped></style>
