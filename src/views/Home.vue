<template>
  <h1>Home</h1>
  <nav class="navigation">
      <router-link
        to="/quiz"
        exact-active-class="navigation__link--exact-active"
        v-on:mouseover="overQuiz"
        v-on:mouseout="outQuiz"
        v-bind:class="{ judgequiz: judgeQuiz, navigation__link: navigationLink.quiz}"
        >Vue クイズ</router-link
      >|
      <router-link
        to="/palette"
        exact-active-class="navigation__link--exact-active"
        v-on:mouseover="overPalette"
        v-on:mouseout="outPalette"
        v-bind:class="{ judgepalette: judgePalette, navigation__link: navigationLink.palette}"
        >Vue パレット</router-link
      >|
      <router-link
        to="/memo"
        exact-active-class="navigation__link--exact-active"
        v-on:mouseover="overMemo"
        v-on:mouseout="outMemo"
        v-bind:class="{ judgememo: judgeMemo, navigation__link: navigationLink.memo}"
        >Vue メモ</router-link
      >
    </nav>
</template>

<script>
  export default{
    data(){
      return{
        judgeQuiz: false,
        judgePalette: false,
        judgeMemo: false,
        navigationLink:{
          quiz: true,
          palette: true,
          memo: true
        },
      }
    },
    methods: {
      overQuiz: function(){
        this.judgeQuiz=true
        this.navigationLink.quiz=false
      },
      outQuiz:function(){
        this.judgeQuiz=false
        this.navigationLink.quiz=true
      },
      overPalette: function(){
        this.judgePalette=true
        this.navigationLink.palette=false
      },
      outPalette:function(){
        this.judgePalette=false
        this.navigationLink.palette=true
      },
      overMemo: function(){
        this.judgeMemo=true
        this.navigationLink.memo=false
      },
      outMemo:function(){
        this.judgeMemo=false
        this.navigationLink.memo=true
      },
    },
  }
</script>

<style>
.navigation {
  display: flex;
  justify-content: center;
  align-items: flex-end;
  gap: 0.8rem;
  font-size: 1.5rem;
}

.judgequiz{
  color: blue;
  font-size: 2rem;
  font-weight: bold;
}

.judgepalette{
  color: blue;
  font-size: 2rem;
  font-weight: bold;
}

.judgememo{
  color: blue;
  font-size: 2rem;
  font-weight: bold;
}

.navigation__link {
  font-weight: bold;
  color: #2c3e50;
}

</style>