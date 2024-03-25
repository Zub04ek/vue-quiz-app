<template>
  <header class="mt-5 flex justify-between items-baseline gap-40">
    <h4 class="text-[30px]">Question {{ questionStatus }}</h4>
    <div class="flex-1 w-[300px] h-[10px] border border-lime-600 rounded-full">
      <div :style="{ width: barPercentage }" class="h-full bg-lime-600"></div>
    </div>
  </header>
</template>

<script setup>
import { defineProps } from 'vue'

const { questionStatus, barPercentage } = defineProps(['questionStatus', 'barPercentage'])
</script>

<style scoped></style>
