<template>
	<div class="quiz__questions">
      <div class="quiz__progress">
        <div class="quiz__bar"></div>
        <div class="quiz__status">1 out of 3 questions answered</div>
      </div>
      <div
				class="quiz__wrap"
				v-for="question in questions"
				:key="question.q"
			>
        <div class="quiz__question">{{ question.q }}</div>
        <ul class="quiz__answers">
          <li
						class="quiz__answer"
						v-for="answer in question.answers"
						:key="answer.text"
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
		}
	}
}
</script>