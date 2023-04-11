<script setup>
import { defineProps, defineEmits } from "vue"
const { question } = defineProps(["question"])
const emit = defineEmits(["selectOption"])
const emitSelectedOption = (isCorrect) => {
  emit("selectOption", isCorrect)
}
</script>

<template>
  <div class="question-container">
    <h1 class="question">{{ question.text }}</h1>
  </div>
  <div
    v-for="option in question.options"
    :key="option.id"
    class="options-container"
    @click="emitSelectedOption(option.isCorrect)"
  >
    <div class="option">
      <p class="options-label">{{ option.label }}</p>
      <div class="options-value">
        <p>{{ option.text }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.question-container {
  margin-top: 20px;
}
.question {
  font-size: 40px;
  margin-bottom: 20px;
}
.option {
  display: flex;
  margin-bottom: 20px;
  cursor: pointer;
}
.options-label {
  background-color: bisque;
  width: 50px;
  height: 50px;
  font-size: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.options-value {
  background-color: rgb(244, 239, 239);
  width: 100%;
  font-size: 30px;
  padding: 0;
}
</style>
