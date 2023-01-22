<template>
	<div class="quiz__questions">
      <div class="quiz__progress">
        <div class="quiz__bar" :style="{ width: `${(questionAnswered / questions.length) * 100}%` }"></div>
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

<script>
export default {
	name: 'Questions',
	props: {
		questions: {
			type: Array,
		},
		questionAnswered: {
			type: Number
		}
	},
	emits: ['question-answered'],
	methods: {
		selectAnswer(is_correct) {
			this.$emit('question-answered', is_correct);
		}
	}
}
</script>