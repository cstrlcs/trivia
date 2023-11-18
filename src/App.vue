<script setup>
import { ref, computed } from 'vue'
import TriviaQuestion from './components/TriviaQuestion.vue'
import TriviaAnswers from './components/TriviaAnswers.vue'
import TriviaResult from './components/TriviaResult.vue'

const questions = ref(null)
const currentQuestion = ref(0)
const correctAnswers = ref([])

const computedQuestion = computed(() => questions.value[currentQuestion.value])

const validateAnswer = (answer) => {
  if (answer === computedQuestion.value.answer) {
    correctAnswers.value.push(answer)
  }

  currentQuestion.value = currentQuestion.value + 1
}

fetch('https://simple-trivia.up.railway.app')
  .then(response => response.json())
  .then(data => questions.value = data)
</script>

<template>
  <main v-if="questions">
    <TriviaQuestion 
      v-if="computedQuestion"
      :question="computedQuestion"
      @answer="validateAnswer" 
    />

    <TriviaResult
      v-else
      :correct-answers-total="correctAnswers.length"
      :questions-total="questions.length"
    />
    
    <TriviaAnswers :correct-answers="correctAnswers" />
  </main>
</template>

<style>
body {
  background-color: rgb(250, 250, 250)
}

main {
  font-family: Inter, sans-serif;
  text-align: center;
  margin: auto;
  max-width: 600px;
  padding: 32px;
}
</style>
