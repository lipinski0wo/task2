<template>
  <div class="color-picker">
    <button
      class="color-picker__element"
      :class="{ 'color-picker__element--selected': index === selected }"
      v-for="(gradient, index) in gradients"
      :key="index"
      v-on:click="selected = index"
    >
      <div
        class="color-picker__gradient"
        :style="{
          background: `linear-gradient(0deg, ${gradient.join(', ')})`,
        }"
      ></div>
    </button>
  </div>
</template>

<script>
export default {
  data: () => ({
    selected: 0,
  }),
  props: {
    gradients: {
      type: Array,
      default: () => [
        ["red", "green", "pink"],
        ["orange", "purple", "black"],
        ["grey", "blue", "yellow"],
        ["brown", "white", "brown"],
      ],
    },
  },
};
</script>

<style scoped>
.color-picker {
  display: flex;
  flex-direction: row;
}

.color-picker__element {
  background: transparent;
  border: 1px solid transparent;
  padding: 3px;
  width: 17px;
  height: 22px;
  box-sizing: border-box;
}

.color-picker__gradient {
  width: 100%;
  height: 100%;
}

.color-picker__element--selected {
  border-color: #000;
}
</style>
