<template>
  <h1>Vue パレット</h1>
  <div class="app">
    <div
      class="palette"
      v-bind:style="{ backgroundColor: `rgba(${red}, ${green}, ${blue}, 0.5)` }"
      v-on:click="colorDecision"
      v-on:mousemove="colorChange"
    ></div>
    <p>rgba( {{ red }}, {{ green }}, {{ blue }}, 0.5 )</p>
    <!-- rangeで色を指定できるようにした -->
    <div class="red">赤</div>
    <input type="range" min="0" max="255" v-model="red" />
    <div class="green">緑</div>
    <input type="range" min="0" max="255" v-model="green" />
    <div class="blue">青</div>
    <input type="range" min="0" max="255" v-model="blue" />
    <button v-on:click="colorDecision" class="color-decision">
      この色に決定
    </button>
    <div class="colors-container">
      <div
        v-for="color in colors"
        v-bind:key="color"
        v-bind:color="color"
        v-bind:style="{
          backgroundColor: `rgba(${color.red}, ${color.green}, ${color.blue}, 0.5)`,
        }"
        class="mini-palette"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      red: 0,
      green: 0,
      blue: 0,
      colors: [],
    }
  },
  methods: {
    colorDecision: function () {
      this.colors.push({ red: this.red, green: this.green, blue: this.blue })
    },
    //paletteの位置でX座標で赤,Y座標で緑が変わる
    colorChange: function (e) {
      this.red = e.offsetX
      this.green = e.offsetY
    },
  },
}
</script>

<style>
.app {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
}
.palette {
  width: 255px;
  height: 255px;
}
.red {
  color: red;
}
.green {
  color: green;
}
.blue {
  color: blue;
}
.color-decision {
  margin-top: 1%;
}
.mini-palette {
  min-width: 60px;
  height: 60px;
}
.colors-container {
  display: flex;
  flex-wrap: wrap;
  width: 300px;
  padding-top: 8px;
}
</style>
