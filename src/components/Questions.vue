<script>
export default {
  name: "Questions",
  props: ["questions","questionsAnswered"],
  emits: ["question_answered"],
  methods: {
    selectAnswer(is_correct){
      this.$emit("question_answered", is_correct);
    }
  }
}
</script>

<template>
  <div class="questions-ctr">
    <div class="progress">
      <div class="bar" :style="{ width: `${(questionsAnswered / questions.length) * 100}%`}"></div>
      <div class="status">{{ questionsAnswered }} out of {{ questions.length }} questions answered</div>
    </div>
    <div class="single-question" v-for="(question, qi) in questions" :key="question.q" v-show="questionsAnswered == qi">
      <div class="question">{{ question.q }}</div>
      <div class="answers" v-for="answer in question.answers" :key="answer.text">
        <div class="answer" @click.prevent="selectAnswer(answer.is_correct)">{{ answer.text }}</div>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>