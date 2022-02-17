<template>
  <div class="general-tile">
    <div class="general-tile__wrapper">
      <img
        class="general-tile__image"
        :src="require(`@/assets/${shoe.name}.png`)"
      />
      <h3>{{ shoe.name }}</h3>
      <p>{{ shoe.description }}</p>

      <div class="general-tile__info">
        <span>200 CHF</span>|
        <span>Neon & Grey</span>
      </div>
      <color-picker />
    </div>
    <general-button class="general-tile__action" @click="callForAction">
      Shop now
    </general-button>
  </div>
</template>

<script>
import GeneralButton from "../Buttons/GeneralButton.vue";
import ColorPicker from "../Pickers/ColorPicker.vue";

export default {
  props: {
    shoe: {
      type: Object,
      default: () => ({
        name: "name",
        description: "a really nice default description should go here",
        price: 200,
        id: "",
      }),
    },
  },
  name: "GeneralTile",
  components: {
    GeneralButton,
    ColorPicker,
  },
  methods: {
    callForAction() {
      window
        .open("https://www.youtube.com/watch?v=dQw4w9WgXcQ", "_blank")
        .focus();
    },
  },
};
</script>

<style scoped>
.general-tile {
  width: 100%;
  max-width: 350px;
  margin: 20px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.general-tile__wrapper {
  background: #f7f7f7;
  padding: 10px;
  box-sizing: border-box;
  margin-bottom: 20px;
}

.general-tile__image {
  width: 100%;
  height: auto;
}

.general-tile__action {
  background: #3c6473;
  width: 80%;
}

.general-tile__info {
  margin: 15px 0;
}

.general-tile__info span {
  margin-right: 10px;
}
</style>
