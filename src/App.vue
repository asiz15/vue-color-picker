<template>
  <div id="app">
    <h3 style="margin-bottom: 3px">Vue JS Color picker</h3>
    <p style="margin-bottom: 7%">
      A component with <b>v-model support </b>for pick colors.
    </p>
    <ColorPicker v-model="color" round :size="50"></ColorPicker>
    <h4>{{ color }}</h4>
  </div>
</template>

<script>
import ColorPicker from "./components/ColorPicker";

export default {
  name: "App",
  components: {
    ColorPicker,
  },
  data() {
    return {
      color: null,
    };
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
