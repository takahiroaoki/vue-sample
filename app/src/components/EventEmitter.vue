<script setup lang="ts">
import { ref } from 'vue'
const emit = defineEmits(['buttonPushed'])

const payload = ref<HTMLInputElement | null>(null)
const onClick = () => {
	emit('buttonPushed', payload.value!.value)
}

defineExpose({
	doSomething(value: string) {
		console.log(value)
	},
})
</script>

<template>
	<input ref="payload" type="text" placeholder="payload">
	<button @click="onClick">emit event</button>
</template>