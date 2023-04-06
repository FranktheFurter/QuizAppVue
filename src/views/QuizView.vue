<script setup>
import Question from "../components/Question.vue"
import QuizHeader from "../components/QuizHeader.vue"
import quizzes from "../data/quizzes.json"
import { useRoute } from "vue-router"
import { ref } from "vue"
const route = useRoute()
const quizId = parseInt(route.params.id)
const quiz = quizzes.find((quiz) => quiz.id === quizId)
const currentQuestion = ref(0)
</script>
<template>
  <div>
    <QuizHeader />
    <div>
      <Question :question="quiz.questions[currentQuestion]" />
    </div>
  </div>
</template>

<style scoped></style>
