<template>
  <div class="results-screen">
    <h3 class="results-screen__text">Congratulations !</h3>
    <note class="results-screen__text results-screen__note"
      >Based on your selection we've decided on the {{ ratedShoes[0].name }}!
      Enjoy the 30 day trial!</note
    >
    <general-tile :shoe="ratedShoes[0]" />
    <h3 class="results-screen__text">Similar profiles</h3>
    <general-tile
      v-for="shoe in ratedShoes.slice(1)"
      :key="shoe.id"
      :shoe="shoe"
    />

    <button
      class="results-screen__restart-action"
      @click="$emit('restartQuiz')"
    >
      Restart Quiz
    </button>
  </div>
</template>

<script>
import GeneralTile from "../Atoms/Tiles/GeneralTile.vue";
import Note from "../Atoms/Texts/Note.vue";

export default {
  name: "ResultsScreen",
  props: {
    ratedShoes: Array,
  },
  components: {
    GeneralTile,
    Note,
  },
};
</script>

<style scoped>
.results-screen {
  height: 100%;
  overflow: hidden;
  background: #fff;
  padding: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  box-sizing: border-box;
}

.results-screen__loader {
  margin-top: -170px;
  width: 50px;
}

.results-screen__note {
  letter-spacing: 1px;
  color: #fff;
  font-size: 15px;
}

.results-screen__text {
  width: 95%;
}

.results-screen__note {
  font-size: 15px;
  color: rgba(0, 0, 0, 0.6);
}

.results-screen__restart-action {
  background: transparent;
  border-color: transparent;
}
</style>
