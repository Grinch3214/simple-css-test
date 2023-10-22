<template>
	<div class="quiz__result">
      <div class="quiz__title">{{ props.results[resultIndex].title }}</div>
      <div class="quiz__desc">{{ props.results[resultIndex].desc }}</div>
    </div>
</template>

<script setup>
	import { computed } from 'vue'

	const props = defineProps({
		totalCorrect: {
			type: Number,
		},
		results: {
			type: Array,
		}
	})

	const resultIndex = computed(() => {
		let index = 0;

		props.results.forEach((element, inx) => {
			if(element.min <= props.totalCorrect && element.max >= props.totalCorrect) {
				index = inx;
			}
		});
		
		return index;
	})

</script>