<script setup lang="ts">
import { ref, computed } from 'vue'

const price = ref(0)
const incrementPrice = (): void => {
  price.value += 1
}

const info = ref({
  'count': 0
})
const incrementCount = (): void => {
  info.value.count += 1
}

const componentId = ref('component__id')

const userInput = ref('')

const score = ref(0)
const evaluation = computed(() => (
  score.value % 2 == 0 ? 'Even' : 'Odd'
))
</script>

<template>
  <section>ref function</section>
  <p>Price: {{ price }}</p>
  <button @click="incrementPrice">increment price</button>

  <p>Count: {{ info.count }}</p>
  <button @click="incrementCount">increment count</button>

  <section>directive</section>
  <p :componentId>component</p>
  <p v-bind="{ componentId }">component</p>
  <p>{{ info.count }}</p>
  <input type="text" @keyup="info.count++" />

  <p>{{ userInput }}</p>
  <input v-model="userInput" type="text">

  <p>{{ evaluation }}</p>
  <p>{{ score }}</p>
  <button @click="score++">count up</button>
</template>

<style scoped></style>
