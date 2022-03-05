<template>
  <h1>誕生日クイズ！！！！！</h1>
  <div class="app">
    <h2>かいとの誕生日は！？</h2>
    <img class="quiz-image" src="../assets/kaito.jpg" alt="クイズタイトル" />
    <div class="container">
      <button
        class="btn btn--orange btn--cubic btn--shadow"
        v-on:click="oneFirst"
      >
        {{ "2月19日" }}
      </button>
      <button
        class="btn btn--pink btn--cubic btn--shadow"
        v-on:click="twoFirst"
      >
        {{ "4月13日" }}
      </button>
      <button
        class="btn btn--blue btn--cubic btn--shadow"
        v-on:click="threeFirst"
      >
        {{ "7月29日" }}
      </button>
      <button
        class="btn btn--yellow btn--cubic btn--shadow"
        v-on:click="fourFirst"
      >
        {{ "10月24日" }}
      </button>
    </div>
    <div v-if="answer1">{{ answer1 }}</div>
  </div>

  <div class="app">
    <h2>こうへいの誕生日は！？</h2>
    <img class="quiz-image" src="../assets/kohei.jpg" alt="クイズタイトル" />
    <div class="container">
      <button
        class="btn btn--orange btn--cubic btn--shadow"
        v-on:click="oneSecond"
      >
        {{ "2月19日" }}
      </button>
      <button
        class="btn btn--pink btn--cubic btn--shadow"
        v-on:click="twoSecond"
      >
        {{ "4月13日" }}
      </button>
      <button
        class="btn btn--blue btn--cubic btn--shadow"
        v-on:click="threeSecond"
      >
        {{ "7月29日" }}
      </button>
      <button
        class="btn btn--yellow btn--cubic btn--shadow"
        v-on:click="fourSecond"
      >
        {{ "10月24日" }}
      </button>
    </div>
    <div v-if="answer2">{{ answer2 }}</div>
  </div>

  <div class="app">
    <h2>あきとの誕生日は！？</h2>
    <img class="quiz-image" src="../assets/akito.png" alt="クイズタイトル" />
    <div class="container">
      <button
        class="btn btn--orange btn--cubic btn--shadow"
        v-on:click="oneThird"
      >
        {{ "2月19日" }}
      </button>
      <button
        class="btn btn--pink btn--cubic btn--shadow"
        v-on:click="twoThird"
      >
        {{ "4月13日" }}
      </button>
      <button
        class="btn btn--blue btn--cubic btn--shadow"
        v-on:click="threeThird"
      >
        {{ "7月29日" }}
      </button>
      <button
        class="btn btn--yellow btn--cubic btn--shadow"
        v-on:click="fourThird"
      >
        {{ "10月24日" }}
      </button>
    </div>
    <div v-if="answer3">{{ answer3 }}</div>
  </div>

  <div class="app">
    <h2>さっきーの誕生日は！？</h2>
    <img
      class="quiz-image"
      src="../assets/sacky1.jpg
      "
      alt="クイズタイトル"
    />
    <img
      class="quiz-image"
      src="../assets/sacky2.jpg
      "
      alt="クイズタイトル"
    />
    <div class="container">
      <button
        class="btn btn--orange btn--cubic btn--shadow"
        v-on:click="oneFourth"
      >
        {{ "2月19日" }}
      </button>
      <button
        class="btn btn--pink btn--cubic btn--shadow"
        v-on:click="twoFourth"
      >
        {{ "4月13日" }}
      </button>
      <button
        class="btn btn--blue btn--cubic btn--shadow"
        v-on:click="threeFourth"
      >
        {{ "7月29日" }}
      </button>
      <button
        class="btn btn--yellow btn--cubic btn--shadow"
        v-on:click="fourFourth"
      >
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

.btn--orange {
  color: #fff;
  background-color: #eb6100;
  border-bottom: 5px solid #b84c00;
}
.btn--orange:hover {
  margin-top: 3px;
  color: #fff;
  background: #f56500;
  border-bottom: 2px solid #b84c00;
}
.btn--pink {
  color: #fff;
  background-color: #e615e6;
  border-bottom: 5px solid #c5029b;
}
.btn--pink:hover {
  margin-top: 3px;
  color: #fff;
  background-color: #e615e6;
  border-bottom: 2px solid #da00e6;
}
.btn--yellow {
  color: #fff;
  background-color: #f0d612;
  border-bottom: 5px solid #b8a201;
}
.btn--yellow:hover {
  margin-top: 3px;
  color: #fff;
  background-color: #f0d612;
  border-bottom: 2px solid #b8a201;
}
.btn--blue {
  color: #fff;
  background-color: #0b2ce9;
  border-bottom: 5px solid #3600a2;
}
.btn--blue:hover {
  margin-top: 3px;
  color: #fff;
  background-color: #0b2ce9;
  border-bottom: 2px solid #3600a2;
}
.btn--shadow {
  -webkit-box-shadow: 0 3px 5px rgba(0, 0, 0, 0.3);
  box-shadow: 0 3px 5px rgba(0, 0, 0, 0.3);
}
</style>
