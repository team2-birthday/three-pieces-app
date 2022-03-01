<template>
  <h1>Vue パレット</h1>
  <div class="app">
    <div
      class="palette"
      v-bind:style="{
        backgroundColor: `rgba(${red}, ${green}, ${blue}, ${opacity})`,
      }"
      v-on:click="colorDecision"
      v-on:mousemove="colorChange"
    ></div>
    <p>rgba( {{ red }}, {{ green }}, {{ blue }}, {{ opacity }} )</p>
    <!-- rangeで色を指定できるようにした -->
    <div class="red">赤</div>
    <input type="range" min="0" max="255" v-model="red" />
    <div class="green">緑</div>
    <input type="range" min="0" max="255" v-model="green" />
    <div class="blue">青</div>
    <input type="range" min="0" max="255" v-model="blue" />
    <div class="opacity">透明度</div>
    <input type="range" min="0" max="1" step="0.01" v-model="opacity" />
    <button v-on:click="colorDecision" class="color-decision">
      この色に決定
    </button>
    <div class="colors-container">
      <div
        v-for="color in colors"
        v-bind:key="color"
        v-bind:color="color"
        v-bind:style="{
          backgroundColor: `rgba(${color.red}, ${color.green}, ${color.blue}, ${color.opacity})`,
        }"
        v-on:click="pastColorDecision(color)"
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
      opacity: 1,
      colors: [],
    }
  },
  methods: {
    colorDecision: function () {
      this.colors.push({
        red: this.red,
        green: this.green,
        blue: this.blue,
        opacity: this.opacity,
      })
    },
    //paletteの位置でX座標で赤,Y座標で緑が変わる
    colorChange: function (e) {
      this.red=e.offsetX
      this.green=e.offsetY
    },
    // クリックしたミニパレットの色をパレットに表示する
    pastColorDecision: function (color) {
      this.red = color.red
      this.green = color.green
      this.blue = color.blue
      this.opacity = color.opacity
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
  font-size: 1.5em;
  text-align: center;
  line-height: 0.95em;
  font-weight: bold;
  color: transparent;
  background: repeating-linear-gradient(
    0deg,
    #c62828 0.1em,
    #ef5350 0.2em,
    #ffebee 0.3em,
    #ef5350 0.4em,
    #c62828 0.5em
  );
  -webkit-background-clip: text;
}
.green {
  font-size: 1.5em;
  text-align: center;
  line-height: 0.95em;
  font-weight: bold;
  color: transparent;
  background: repeating-linear-gradient(
    0deg,
    #28c635 0.1em,
    #3fdf54 0.2em,
    #ffebee 0.3em,
    #50ef85 0.4em,
    #28c628 0.5em
  );
  -webkit-background-clip: text;
}
.blue {
  font-size: 1.5em;
  text-align: center;
  line-height: 0.95em;
  font-weight: bold;
  color: transparent;
  background: repeating-linear-gradient(
    0deg,
    #0277bd 0.1em,
    #4fc3f7 0.2em,
    #e1f5fe 0.3em,
    #4fc3f7 0.4em,
    #0277bd 0.5em
  );
  -webkit-background-clip: text;
}
.opacity {
  font-size: 1.5em;
  text-align: center;
  line-height: 0.95em;
  font-weight: bold;
  color: #fff;
  text-shadow: 0 0 0.2em rgba(0, 0, 0, 1);
}
.color-decision {
  margin-top: 1%;
  position: relative;
  display: inline-block;
  text-decoration: none;
  padding: 0 30px;
  font-size: 19px;
  height: 40px;
  line-height: 40px!;
  background: #24242c;
  font-size: 20px;
  color: rgb(6, 241, 131);
  transition: 0.4s;
  border: none;
}
.color-decision:before {
  position: absolute;
  content: "";
  left: 0;
  top: 0;
  width: 0;
  height: 0;
  border: none;
  border-left: solid 21px white;
  border-bottom: solid 41px transparent;
  z-index: 1;
  transition: 0.4s;
}
.color-decision:after {
  position: absolute;
  content: "";
  right: 0;
  top: 0;
  width: 0;
  height: 0;
  border: none;
  border-left: solid 21px transparent;
  border-bottom: solid 41px white;
  z-index: 1;
  transition: 0.4s;
}
.color-decision:hover:before,
.color-decision:hover:after {
  border-left-width: 25px;
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
