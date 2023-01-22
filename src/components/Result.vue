<template>
	<div class="quiz__result">
      <div class="quiz__title">{{ results[resultIndex].title }}</div>
      <div class="quiz__desc">{{ results[resultIndex].desc }}</div>
    </div>
</template>

<script>
export default {
	name: 'Result',
	props: {
		totalCorrect: {
			type: Number,
		},
		results: {
			type: Array,
		}
	},
	computed: {
		resultIndex() {
			let index = 0;

			this.results.forEach((element, inx) => {
				if(element.min <= this.totalCorrect && element.max >= this.totalCorrect) {
					index = inx;
				}
			});
			
			return index;
		}
	}
}
</script>