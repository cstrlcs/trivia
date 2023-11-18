<script setup>
import TriviaButton from './TriviaButton.vue'

defineProps({
  question: Object
})

const emit = defineEmits(['answer'])
</script>

<template>
  <div>
    <p>{{ question.text }}</p>
    
    <div>
      <TriviaButton
        v-for="option in question.options" 
        @click="emit('answer', option)"
      >
        {{ option }}
      </TriviaButton>
    </div>
  </div>
</template>

<style scoped>
p {
  font-size: 32px;
  font-weight: bold;
}
</style>
