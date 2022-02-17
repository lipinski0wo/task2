<template>
  <div class="quiz">
    <initial-screen
      v-if="quizState === 'init'"
      v-on:onStartQuiz="quizState = 'active'"
    />
    <question-screen
      v-if="quizState === 'active'"
      :copy="questions[questionIndex].copy"
      :answers="questionScreenAnswers"
      v-on:onAnswerSelect="handleAnswer"
    />
    <pending-screen v-if="quizState === 'pending'" />
    <results-screen
      v-if="quizState === 'results'"
      :ratedShoes="ratedShoes"
      @restartQuiz="restartQuiz"
    />
  </div>
</template>

<script>
import InitialScreen from "./InitialScreen.vue";
import QuestionScreen from "./QuestionScreen.vue";
import PendingScreen from "./PendingScreen.vue";
import ResultsScreen from "./ResultsScreen.vue";

export default {
  name: "Quiz",
  props: {
    questions: Array,
  },

  components: {
    InitialScreen,
    QuestionScreen,
    PendingScreen,
    ResultsScreen,
  },
  data: () => ({
    quizState: "init",
    questionIndex: 0,
    ratings: {},
    ratedShoes: null,
  }),
  computed: {
    questionScreenAnswers() {
      return this.questions[this.questionIndex].answers.map(({ copy }) => copy);
    },
  },
  methods: {
    handleAnswer(selectedAnswerIndex) {
      const { ratingIncrease, nextQuestion } =
        this.questions[this.questionIndex].answers[selectedAnswerIndex];

      this.updateRatings(ratingIncrease);

      if (nextQuestion === "") {
        this.quizState = "pending";

        this.$emit("getShoesForRating", this.ratings, (ratedShoes) => {
          this.ratedShoes = ratedShoes;
          this.quizState = "results";
        });
        return;
      }

      this.questionIndex = nextQuestion;
    },
    updateRatings(ratingIncrease) {
      const entries = Object.entries(ratingIncrease);

      this.ratings = entries.reduce((acc, [key, value]) => {
        const oldRatingValue = acc[key] || 0;

        acc[key] = oldRatingValue + value;

        return acc;
      }, this.ratings);
    },
    restartQuiz() {
      this.quizState = "init";
      this.questionIndex = 0;
      this.ratings = {};
      this.ratedShoes = null;
    },
  },
};
</script>

<style scoped>
.quiz {
  height: 100%;
}
</style>
