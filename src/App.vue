<template>

  <h1>Ninja Reaction Timer</h1>
  <button @click="start" v-bind:disabled="isPlaying">Play</button>
  <BlockOne v-if="isPlaying" v-bind:delay="delay" @record="recordTime"/>
  <ResultsOne v-if="showResults" :reactionTime="score"/>
</template>

<script>

import BlockOne from './components/BlockOne.vue'
import ResultsOne from './components/ResultsOne.vue'


export default {
  name: 'App',
  components: { BlockOne, ResultsOne },
  data (){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true;
      this.showResults = false;
    },
    recordTime(time){
      this.score = time;
      this.isPlaying = false;
      this.showResults = true;
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
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
