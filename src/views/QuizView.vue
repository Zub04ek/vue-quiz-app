<template>
  <div>
    <QuizHeader :questionStatus="questionStatus" :barPercentage="barPercentage" />
    <div>
      <Question
        v-if="!showResults"
        :question="quiz.questions[currentQuestionIndex]"
        @selectOption="onOptionSelected"
      />
      <QuizResult
        v-else
        :quizQuestionsLength="quiz.questions.length"
        :numberOfCorrectAnswers="numberOfCorrectAnswers"
      />
    </div>
  </div>
</template>

<script setup>
import Question from '../components/QuestionItem.vue'
import QuizHeader from '../components/QuizHeader.vue'
import QuizResult from '../components/QuizResult.vue'
import { useRoute } from 'vue-router'
import quizes from '../data/quizes.json'
import { ref, computed } from 'vue'

const route = useRoute()
const quizId = parseInt(route.params.id)
const quiz = quizes.find((q) => q.id === quizId)
const currentQuestionIndex = ref(0)
const numberOfCorrectAnswers = ref(0)
const showResults = ref(false)

const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`)
const barPercentage = computed(
  () => `${(currentQuestionIndex.value / quiz.questions.length) * 100}%`
)

const onOptionSelected = (isCorrect) => {
  if (isCorrect) {
    numberOfCorrectAnswers.value++
  }
  if (quiz.questions.length - 1 === currentQuestionIndex.value) {
    showResults.value = true
  }
  currentQuestionIndex.value++
}
</script>

<style scoped></style>
