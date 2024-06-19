<script setup lang="ts">
import { ref, computed, watchEffect, watch, onMounted } from 'vue'
import Greeting from './components/Greeting.vue'
import EventEmitter from './components/EventEmitter.vue'

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

const countWatch = ref(0)
watchEffect(() => {
  console.log('countWatch was modified!')
  console.log(countWatch.value)
})

const countWatch2 = ref(0)
watch(countWatch2, (newValue, oldValue) => {
  console.log('new: ', newValue)
  console.log('old: ', oldValue)
})

watch(
  () => (countWatch.value + countWatch2.value),
  (newValue, oldValue) => {
    console.log('watch 2 values sum')
    console.log('new: ', newValue)
    console.log('old: ', oldValue)
  }
)

const greeting1 = ref('hello')

const emitter = ref<InstanceType<typeof EventEmitter> | null>(null)
  const onEmit = (payload: string) => {
  emitter.value!.doSomething(payload + 'is called from App.vue!')
}

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

  <p>{{ countWatch }}</p>
  <button @click="countWatch++">count up</button>

  <p>{{ countWatch2 }}</p>
  <button @click="countWatch2++">count up</button>

  <Greeting v-bind="{ greeting1: greeting1, greeting2: 'good morning' }" />
  <Greeting :greeting1="greeting1" greeting2="good morning2" />
  <button @click="greeting1 = 'changed!'">change greeting1</button>

  <EventEmitter ref="emitter" @button-pushed="onEmit"></EventEmitter>
</template>

<style scoped></style>
