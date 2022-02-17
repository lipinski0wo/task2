<template>
  <div class="question-screen">
    <note class="question-screen__note"
      >TRY ON QUIZ<br />
      30 DAYS RISK FREE</note
    >
    <Header class="question-screen__header">{{ copy }}</Header>

    <div class="question-screen__action-buttons">
      <outlined-button
        v-for="(answer, index) in answers"
        :key="answer"
        class="question-screen__action-button"
        @click="$emit('onAnswerSelect', index)"
      >
        {{ answer }}
      </outlined-button>
    </div>
  </div>
</template>

<script>
import OutlinedButton from "../Atoms/Buttons/OutlinedButton.vue";
import Note from "../Atoms/Texts/Note.vue";
import Header from "../Atoms/Texts/Header.vue";

export default {
  name: "QuestionScreen",
  props: {
    copy: String,
    answers: Array,
  },
  components: {
    OutlinedButton,
    Note,
    Header,
  },
};
</script>

<style scoped>
.question-screen {
  box-sizing: border-box;
  height: 100%;
  overflow: hidden;
  background: #333;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  padding: 20px;
}

.question-screen__note {
  clear: both;
  display: block;
  text-align: center;
  margin-top: 20px;
  color: #fff;
  letter-spacing: 2.5px;
}

.question-screen__header {
  text-align: center;
  font-size: 20px;
  color: #fff;
  margin-top: 130px;
}

.question-screen__action-buttons {
  margin-top: 105px;
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
}

.question-screen__action-button {
  width: 45%;
  padding: 10px;
}
</style>
