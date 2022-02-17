<template>
  <layout-default>
    <quiz :questions="questions" v-on:getShoesForRating="getShoesForRating" />
  </layout-default>
</template>

<script>
import data from "../data.json";
import LayoutDefault from "./components/Layout/default.vue";
import Quiz from "./components/Quiz/index.vue";

export default {
  name: "App",
  components: {
    LayoutDefault,
    Quiz,
  },
  data: () => ({
    questionIndex: 0,
    surveyFinished: false,
    ratings: {},
    questions: data.questions,
  }),
  methods: {
    async fetchShoesForRating(ratings) {
      // get the results from pseudo backend
      const rawShoesData = data.shoes.reduce((acc, v) => {
        acc[v.id] = v;
        return acc;
      }, {});

      const shoes = Object.entries(ratings)
        .sort((a, b) => b[1] - a[1])
        .map(([key, rating]) => ({
          ...rawShoesData[key],
          rating,
          description:
            "Your perfect partner in the world's lightest fully-cushined shoe for Running Remixed.",
          price: 200,
        }));

      return new Promise((resolve) => {
        setTimeout(() => {
          resolve(shoes);
        }, 2000);
      });
    },
    async getShoesForRating(ratings, callback) {
      const ratedShoes = await this.fetchShoesForRating(ratings);
      callback(ratedShoes);
    },
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
</style>
