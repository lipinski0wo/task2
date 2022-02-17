<template>
  <div class="pending-screen">
    <img src="@/assets/loader.gif" class="pending_screen__loader" />
    <note class="pending_screen__note">We're running to get your results.</note>
  </div>
</template>

<script>
import Note from "../Atoms/Texts/Note.vue";

export default {
  name: "pendingScreen",
  components: {
    Note,
  },
};
</script>

<style scoped>
.pending-screen {
  box-sizing: border-box;
  height: 100%;
  overflow: hidden;
  background: #333;
  padding: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.pending_screen__loader {
  margin-top: -170px;
  width: 50px;
}

.pending_screen__note {
  letter-spacing: 1px;
  color: #fff;
  font-size: 15px;
}
</style>
