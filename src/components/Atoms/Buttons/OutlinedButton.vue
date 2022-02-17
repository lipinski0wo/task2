<template>
  <button class="outlined-button" @click="$emit('click')">
    <slot />
  </button>
</template>

<script>
export default {
  name: "OutlinedButton",
};
</script>

<style scoped>
.outlined-button {
  padding: 10px 32px;
  background: transparent;
  border: 1px solid #000;
  color: #fff;
  font-size: 15px;
  box-shadow: 0px 1px 0px 0px #fff;
}
</style>
