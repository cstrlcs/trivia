<script setup>
import TriviaButton from './TriviaButton.vue'

defineProps({
  correctAnswersTotal: Number,
  questionsTotal: Number
})

const reload = () => {
  window.location.reload()
}
</script>

<template>
  <div>
    <p>
      Você acertou {{ correctAnswersTotal }} de {{ questionsTotal }} perguntas!
    </p>

      <TriviaButton @click="reload">Jogar de novo</TriviaButton>
  </div>
</template>
