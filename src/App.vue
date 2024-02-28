<template>
  <div id="app">
    <h1>Ninja Reaction Time</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
    <Result v-if="showResult" :score="score"/>
    <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  </div>
</template>

<script>
import Block from './components/Block.vue';
import Result from './components/Result.vue';

export default {
  name: 'App',
  components: {
    Block,
    Result
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods: {
    start() {
      this.delay = Math.floor(Math.random() * 5000) + 2000;
      this.isPlaying = true;
      this.showResult = false;

    },
    endGame(reactionTime) {
      this.isPlaying = false;
      this.score = reactionTime;
      this.showResult = true;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button {
  padding: 10px 20px;
  font-size: 20px;
  background-color: #0faf87;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
button:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}
</style>
