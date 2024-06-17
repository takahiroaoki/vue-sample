<script setup lang="ts">
import { ref } from 'vue'

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
</template>

<style scoped></style>
