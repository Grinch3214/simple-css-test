<template>
	<div class="quiz__questions">
      <div class="quiz__progress">
        <div class="quiz__bar" :style="{ width: quizBar }"></div>
        <div class="quiz__status">{{ questionAnswered }} out of {{ questions.length }} questions answered</div>
      </div>
      <div
				class="quiz__wrap"
				v-for="(question, index) in questions"
				:key="question.q"
				v-show="questionAnswered === index"
			>
        <div class="quiz__question">{{ question.q }}</div>
        <ul class="quiz__answers">
          <li
						class="quiz__answer"
						v-for="answer in question.answers"
						:key="answer.text"
						@click.prevent="selectAnswer(answer.is_correct)"
					>
						{{ answer.text }}
					</li>
        </ul>
      </div>
    </div>
</template>

<script setup>
import { computed } from 'vue'

	const props = defineProps({
		questions: {
			type: Array,
		},
		questionAnswered: {
			type: Number
		}
	})

	const emits = defineEmits(['question-answered'])

	const selectAnswer = (is_correct) => {
			console.log(is_correct)
			emits('question-answered', is_correct)
		}

	const quizBar = computed(() => {
		return `${(props.questionAnswered / props.questions.length) * 100}%`
	})
</script>