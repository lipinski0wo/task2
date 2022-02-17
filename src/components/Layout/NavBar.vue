<template>
  <div class="nav-bar">
    <hamburger class="nav-bar__hamburger" />
    <logo class="nav-bar__logo" />
  </div>
</template>

<script>
import Logo from "../Atoms/Icons/Logo.vue";
import Hamburger from "../Atoms/Icons/Hamburger.vue";

export default {
  name: "NavBar",
  components: {
    Logo,
    Hamburger,
  },
};
</script>

<style scoped>
.nav-bar {
  position: relative;
  height: 66px;
  display: flex;
  align-items: center;
  box-shadow: 0px 1px 0px 0px #fff;
}

.nav-bar__hamburger {
  margin-left: 15px;
  margin-top: 6px;
}

.nav-bar__logo {
  position: absolute;
  top: 50%;
  left: 48%;
  transform: translate(-50%, -50%);
}
</style>
