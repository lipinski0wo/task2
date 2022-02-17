<template>
  <div class="wrapper">
    <div v-if="surveyFinished">
      <div v-for="shoe in getShoesByRating" :key="shoe.id">
        {{ shoe }}
        <img :src="require(`@/assets/${shoe.name}.png`)" />
      </div>
    </div>
    <div v-else>
      <div>
        <p>{{ questions[questionIndex].copy }}</p>
        <div>
          <button
            v-for="answer in questions[questionIndex].answers"
            :key="answer.id"
            @click="handleAnswer(answer)"
          >
            {{ answer.copy }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import data from "../data.json";

export default {
  name: "App",
  data: () => ({
    questionIndex: 0,
    surveyFinished: false,
    ratings: {},
    questions: data.questions,
    shoes: data.shoes.reduce((acc, v) => {
      acc[v.id] = v;
      return acc;
    }, {}),
  }),
  computed: {
    getShoesByRating() {
      const shoesNames = Object.entries(this.ratings)
        .sort((a, b) => b[1] - a[1])
        .map(([key, rating]) => ({ ...this.shoes[key], rating }));

      return shoesNames;
    },
  },
  methods: {
    handleAnswer({ ratingIncrease, nextQuestion }) {
      this.updateRatings(ratingIncrease);

      if (nextQuestion === "") {
        this.surveyFinished = true;
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
  },
};
</script>
