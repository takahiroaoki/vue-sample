<script setup lang="ts">
defineProps<{
	greeting1: string,
	greeting2: string,
}>()
</script>

<template>
	<section>Greeting Component</section>
	<p>{{ greeting1 }}</p>
	<p>{{ greeting2 }}</p>
</template>