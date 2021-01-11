<template>
  <div>
    <div class="picker-container">
      <div
        :class="[
          'picker-item',
          color == inputValue ? 'picker-item--selected' : '',
        ]"
        v-for="(color, index) in Colors"
        :key="index"
        @click="pickColor(color)"
        :style="{
          backgroundColor: color,
          width: `${Size}px`,
          height: `${Size}px`,
          borderRadius: Type == 'square' ? '0px' : '50%',
        }"
      >
        <img
          v-if="color == inputValue"
          src="../assets/check.png"
          width="16"
          alt=""
          srcset=""
        />
      </div>
    </div>

    <input
      v-show="false"
      @input="onInputChange"
      v-model="inputValue"
      type="text"
    />
  </div>
</template>
<script>
const defaultColors = [
  "#FF6633",
  "#FFB399",
  "#FF33FF",
  "#FFFF99",
  "#00B3E6",
  "#E6B333",
  "#3366E6",
  "#999966",
  "#99FF99",
  "#B34D4D",
  "#80B300",
  "#809900",
  "#E6B3B3",
  "#6680B3",
  "#66991A",
  "#FF99E6",
  "#CCFF1A",
  "#FF1A66",
  "#E6331A",
  "#33FFCC",
  "#66994D",
  "#B366CC",
  "#4D8000",
  "#B33300",
  "#CC80CC",
  "#66664D",
  "#991AFF",
  "#E666FF",
  "#4DB3FF",
  "#1AB399",
  "#E666B3",
  "#33991A",
  "#CC9999",
  "#B3B31A",
  "#00E680",
  "#4D8066",
  "#809980",
  "#E6FF80",
  "#1AFF33",
  "#999933",
];

export default {
  props: {
    value: {
      type: String,
    },
    colors: {
      type: Array,
    },
    size: {
      type: Number,
    },
    round: {
      type: Boolean,
    },
  },
  data() {
    return {
      inputValue: this.value,
    };
  },
  methods: {
    onInputChange() {
      // We will emit the "input" event and pass it the changed value that we wish to be returned to parent component.
      this.$emit("input", this.inputValue);
    },
    pickColor(c) {
      this.inputValue = c;
      this.$emit("input", this.inputValue);
    },
  },
  computed: {
    Colors() {
      if (this.colors) {
        return this.colors;
      }
      return defaultColors;
    },
    Size() {
      if (this.size) {
        return this.size;
      }
      return 33;
    },
    Type() {
      if (this.round) {
        return "circle";
      }
      return "square";
    },
  },
};
</script>
<style lang="scss">
.picker-container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  padding: 0 3% 0 3%;
}
.picker-item {
  width: 30px;
  height: 30px;
  background-color: red;
  margin: 0px 7px 7px 0px;
  cursor: pointer;
  opacity: 0.8;
  display: flex;
  justify-content: center;
  align-items: center;
}
.picker-item--selected {
  opacity: 1 !important;
  transform: scale(1.1);
  border: 1px solid grey;
  transition: all 0.3s;
}
</style>