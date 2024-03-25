<template>
  <header class="mt-[30px] flex items-center">
    <h1 class="font-bold mr-[30px] text-3xl">Quizes</h1>
    <input
      v-model.trim="search"
      type="text"
      name=""
      id=""
      placeholder="Search..."
      class="p-[10px] rounded-xl border-0 bg-slate-200 text-black"
    />
  </header>
  <ul class="flex flex-wrap gap-[35px] mt-10">
    <CardItem v-for="quiz in quizes" :key="quiz.id" :item="quiz" />
  </ul>
</template>

<script setup>
import q from '../data/quizes.json'
import { ref, watch } from 'vue'
import CardItem from '../components/CardItem.vue'

const quizes = ref(q)
const search = ref('')

watch(search, () => {
  quizes.value = q.filter((quiz) => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
})
</script>

<style scoped></style>
