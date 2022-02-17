<template>
  <div class="initial-screen">
    <div class="initial-screen__container">
      <Header>
        Take the quiz <br />
        and try your first pair!
      </Header>
      <general-button @click="$emit('onStartQuiz')"
        >Try On Trial</general-button
      >
      <note class="initial-screen__note">30 Days risk free</note>
    </div>

    <img class="initial-screen__runner" src="@/assets/Runner.png" />
    <div class="initial-screen__fog" />
  </div>
</template>

<script>
import GeneralButton from "../Atoms/Buttons/GeneralButton.vue";
import Note from "../Atoms/Texts/Note.vue";
import Header from "../Atoms/Texts/Header.vue";

export default {
  name: "InitialScreen",
  components: {
    GeneralButton,
    Note,
    Header,
  },
};
</script>

<style scoped>
.initial-screen {
  height: 100%;
  overflow: hidden;
  background: #f7f7f7;
  position: relative;
}

.initial-screen__container {
  padding: 20px;
  margin-top: 56px;
}

.initial-screen__runner {
  position: absolute;
  bottom: 0;
  left: 71%;
  transform: translateX(-50%);
  height: 67%;
  width: auto;
  pointer-events: none;
}

.initial-screen__note {
  clear: both;
  display: block;
  margin-top: 20px;
}

.initial-screen__fog {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 16px;
  background: #f7f7f7;
  box-shadow: 0px -27px 21px 14px rgb(255 255 255 / 40%);
}
</style>
