<template>
	<h1 class="title">Простий тест по CSS</h1>
	<div class="quiz">
		<QuestionsComponent
			v-if="questionAnswered < questions.length"
			:questions="questions"
			:questionAnswered="questionAnswered"
			@question-answered="questionAnswer"
		/>
		<ResultComponent
			v-else
			:totalCorrect="totalCorrect"
			:results="results"
		/>
		<button
			class="quiz__btn"
			@click.prevent="reset"
			v-if="questionAnswered === questions.length"
		>Reset</button>
	</div>
</template>

<script setup>
	import QuestionsComponent from './components/Questions.vue'
	import ResultComponent from './components/Result.vue'
	import { questions, results } from './constants.js'
	import { ref } from 'vue'

	const questionAnswered = ref(0)
	const totalCorrect = ref(0)

	const questionAnswer = (is_correct) => {
		if(is_correct) {
			totalCorrect.value++;
		}
		questionAnswered.value++;
	}

	const reset = () => {
		questionAnswered.value = 0;
		totalCorrect.value = 0;
	}

</script>
