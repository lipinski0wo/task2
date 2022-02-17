<template>
  <div class="layout">
    <div class="layout__navigation">
      <nav-bar />
    </div>
    <div class="layout__content">
      <slot />
    </div>
  </div>
</template>

<script>
import NavBar from "./NavBar.vue";

export default {
  name: "LayoutDefault",
  components: {
    NavBar,
  },
};
</script>

<style scoped>
.layout {
  display: flex;
  flex-direction: column;
  height: 100vh;
}

.layout__navigation {
  z-index: 1;
}

.layout__content {
  flex: 1;
}
</style>
