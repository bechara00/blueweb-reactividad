<script setup>
import { ref, computed } from 'vue'

const counter = ref(0)

const increment = () => {
  counter.value++
}
const decrement = () => {
  counter.value--
}

const reset = () => counter.value = 0

const classCounter = computed(() => {
  if (counter.value === 0) {
    return 'zero'
  }
  if (counter.value > 0) {
    return 'positive'
  }
  if (counter.value < 0) {
    return 'negative'
  }
})


</script>

<template>
  <h1>REACTIVIDAD</h1>
  <h2 :class="classCounter">{{ counter }}</h2>
  <button @click="increment">Aumentar Contador</button>
  <button @click="decrement">Disminuir Contador</button>
  <button @click="reset">Restear Contador</button>
</template>

<style scoped>
.positive {
  color: green
}

.negative {
  color: red
}

.zero {
  color: peru
}
</style>
