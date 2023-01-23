<template>
	<h1 class="title">Простий тест по CSS</h1>
	<div class="quiz">
		<questions
			v-if="questionAnswered < questions.length"
			:questions="questions"
			:questionAnswered="questionAnswered"
			@question-answered="questionAnswer"
		/>
		<result 
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

<script>
import Questions from "./components/Questions.vue";
import Result from './components/Result.vue';

export default {
	name: "App",
	components: {
		Questions,
		Result
	},
	data() {
		return {
			questionAnswered: 0,
			totalCorrect: 0,
			questions: [
				{
					q: 'Як зробити такий відступ: padding-top:10px, padding-bottom: 20px, padding-left: 5px, padding-right: 8px?',
					answers: [
						{
							text: 'padding: 10px 8px 20px 5px;',
							is_correct: true
						},
						{
							text: 'padding: 10px 20px 5px 8px;',
							is_correct: false
						},
						{
							text: 'padding: 20px 10px 5px 8px;',
							is_correct: false
						},
						{
							text: 'padding: 5px 8px 20px 10px;',
							is_correct: false
						}
					]
				},
				{
					q: 'Яким чином можно додати CSS?',
					answers: [
						{
							text: 'Вбудований стиль ( Inline Styling )',
							is_correct: false
						},
						{
							text: 'Внутрішньої таблиці стилів (Internal Style Sheet)',
							is_correct: false
						},
						{
							text: 'Зовнішньої таблиці стилів (External Style Sheet)',
							is_correct: false
						},
						{
							text: 'Трьома способами вище',
							is_correct: true
						}
					]
				},
				{
					q: 'Який HTML-тег використовується для встановлення внутрішньої таблиці стилю?',
					answers: [
						{
							text: '<css>',
							is_correct: false
						},
						{
							text: '<style>',
							is_correct: true
						},
						{
							text: '<script>',
							is_correct: false
						}
					]
				},
				{
					q: 'Як задати кольор шрифту?',
					answers: [
						{
							text: 'font-color: #fafafa;',
							is_correct: false
						},
						{
							text: 'font-color: red;',
							is_correct: false
						},
						{
							text: 'color: red;',
							is_correct: true
						}
					]
				},
			],
			results: [
				{
					min: 0,
					max: 2,
					title: "Спробуй ще!",
					desc: "Непогано, але ти можеш краще!"
				},
				{
					min: 3,
					max: 4,
					title: "Неймовірно!",
					desc: "Твоє навчання приносить тобі плоди!"
				}
			]
		};
	},
	methods: {
		questionAnswer(is_correct) {
			if(is_correct) {
				this.totalCorrect++;
			}

			this.questionAnswered++;
		},

		reset() {
			this.questionAnswered = 0;
			this.totalCorrect = 0;
		}
	}
};
</script>