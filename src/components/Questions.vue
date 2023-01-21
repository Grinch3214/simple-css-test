<template>
	<div class="quiz__questions">
      <div class="quiz__progress">
        <div class="quiz__bar"></div>
        <div class="quiz__status">1 out of 3 questions answered</div>
      </div>
      <div class="quiz__wrap">
        <div class="quiz__question">Sample Question 1</div>
        <ul class="quiz__answers">
          <li class="quiz__answer">Sample Answer 1</li>
          <li class="quiz__answer">Sample Answer 2</li>
          <li class="quiz__answer">Sample Answer 3</li>
          <li class="quiz__answer">Sample Answer 4</li>
        </ul>
      </div>
    </div>
</template>

<script>
export default {
	name: 'Questions'
}
</script>