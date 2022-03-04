<template>
  <h1>誕生日クイズ！！！！！</h1>
  <div class="app">
    <h2>Q. {{ "かいとの誕生日は！？" }}</h2>
    <img class="quiz-image" src="kaito.jpg" alt="クイズタイトル" />
    <div class="container">
      <button v-on:click="oneFirst">
        {{ "2月19日" }}
      </button>
      <button v-on:click="twoFirst">
        {{ "4月13日" }}
      </button>
      <button v-on:click="threeFirst">
        {{ "7月29日" }}
      </button>
      <button v-on:click="fourFirst">
        {{ "10月24日" }}
      </button>
    </div>
    <div v-if="answer1">{{ answer1 }}</div>
  </div>

  <div class="app">
    <h2>Q. {{ "こうへいの誕生日は！？" }}</h2>
    <img class="quiz-image" src="kohei.jpg" alt="クイズタイトル" />
    <div class="container">
      <button v-on:click="oneSecond">
        {{ "2月19日" }}
      </button>
      <button v-on:click="twoSecond">
        {{ "4月13日" }}
      </button>
      <button v-on:click="threeSecond">
        {{ "7月29日" }}
      </button>
      <button v-on:click="fourSecond">
        {{ "10月24日" }}
      </button>
    </div>
    <div v-if="answer2">{{ answer2 }}</div>
  </div>

  <div class="app">
    <h2>Q. {{ "あきとの誕生日は！？" }}</h2>
    <img class="quiz-image" src="akito.png" alt="クイズタイトル" />
    <div class="container">
      <button v-on:click="oneThird">
        {{ "2月19日" }}
      </button>
      <button v-on:click="twoThird">
        {{ "4月13日" }}
      </button>
      <button v-on:click="threeThird">
        {{ "7月29日" }}
      </button>
      <button v-on:click="fourThird">
        {{ "10月24日" }}
      </button>
    </div>
    <div v-if="answer3">{{ answer3 }}</div>
  </div>

  <div class="app">
    <h2>Q. {{ "さっきーの誕生日は！？" }}</h2>
    <img
      class="quiz-image"
      src="https://via.placeholder.com/300x300"
      alt="クイズタイトル"
    />
    <div class="container">
      <button v-on:click="oneFourth">
        {{ "2月19日" }}
      </button>
      <button v-on:click="twoFourth">
        {{ "4月13日" }}
      </button>
      <button v-on:click="threeFourth">
        {{ "7月29日" }}
      </button>
      <button v-on:click="fourFourth">
        {{ "10月24日" }}
      </button>
    </div>
    <div v-if="answer4">{{ answer4 }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      answer1: false,
      answer2: false,
      answer3: false,
      answer4: false,
    }
  },
  methods: {
    oneFirst: function () {
      this.answer1 = "正解！"
    },
    twoFirst: function () {
      this.answer1 = "間違えんな！"
    },
    threeFirst: function () {
      this.answer1 = "なめてんの？"
    },
    fourFirst: function () {
      this.answer1 = "ねえいい加減にしな？笑"
    },

    oneSecond: function () {
      this.answer2 = "は！？"
    },
    twoSecond: function () {
      this.answer2 = "ちょwwおまwww"
    },
    threeSecond: function () {
      this.answer2 = "そろそろ怒るよ？笑"
    },
    fourSecond: function () {
      this.answer2 = "正解！"
    },

    oneThird: function () {
      this.answer3 = "ん！？"
    },
    twoThird: function () {
      this.answer3 = "正解！"
    },
    threeThird: function () {
      this.answer3 = "けええれええええ！"
    },
    fourThird: function () {
      this.answer3 = "んなわけないだろ"
    },

    oneFourth: function () {
      this.answer4 = "へ！？"
    },
    twoFourth: function () {
      this.answer4 = "あ〜覚えてないとかマジで傷つくわ"
    },
    threeFourth: function () {
      this.answer4 = "正解！"
    },
    fourFourth: function () {
      this.answer4 = "........."
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
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.quiz-image {
  height: 300px;
  width: 300px;
  object-fit: contain;
}

.container {
  display: flex;
  height: 2em;
  width: 300px;
  padding: 1em;
  justify-content: space-around;
}
</style>
