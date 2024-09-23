<script setup>
import { ref, computed } from 'vue'

const counter = ref(0)

const myArray = ref([])


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

const addArray = () => {
  myArray.value.push(counter.value)
  return myArray
}

const valueDisabled = computed(() => {
  if (myArray.value.includes(counter.value)) {
    return true
  }
  else {
    return false
  }

})


</script>

<template>
  <h1>REACTIVIDAD</h1>
  <h2 :class="classCounter">{{ counter }}</h2>
  <button @click="increment">Aumentar Contador</button>
  <button @click="decrement">Disminuir Contador</button>
  <button @click="reset">Restear Contador</button>
  <button :disabled="valueDisabled" @click="addArray">Add</button>
  <h1>Lista de favoritos</h1>
  <ul v-for="(item, index) in myArray" key="index">

    <li >{{ item }}</li>

  </ul>

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
