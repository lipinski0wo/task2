<template>
  <button class="general-button" @click="$emit('click')">
    <slot />
  </button>
</template>

<script>
export default {
  name: "GeneralButton",
};
</script>

<style scoped>
.general-button {
  padding: 10px 32px;
  background: #000;
  color: #fff;
  font-size: 15px;
  box-shadow: 0px 1px 0px 0px #fff;
}
</style>
