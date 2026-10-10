<script setup>
import { ref } from 'vue'
import FoodComponents from './components/FoodCard.vue'

const foods = ref([
	{ name: 'sushi', emoji: '🍣' },
	{ name: 'icecream', emoji: '🍦' },
	{ name: 'パン', emoji: '🍞' },
	{ name: 'とんかつ', emoji: '🐖' },
	{ name: 'そば', emoji: '🍜' },
	{ name: '栗', emoji: '🌰' },
])

const pickedIndex = ref(0)
const newIndex = ref(1)

const pickfood = (index) => {
	pickedIndex.value = index
	newIndex.value++
}
</script>

<template>
	<main>
		<h1>what do you want to eat today?</h1>
		<FoodComponents
			:name="foods[pickedIndex].name"
			:emoji="foods[pickedIndex].emoji"
			@click="pickfood(pickedIndex)"
		/>
		<template v-if="newIndex < foods.length">
			<p>vs</p>
			<FoodComponents
				:name="foods[newIndex].name"
				:emoji="foods[newIndex].emoji"
				@click="pickfood(newIndex)"
			/>
		</template>
	</main>
</template>

<style scoped>
main {
	margin: 100px auto;
	width: 350px;
	text-align: center;
}
</style>
