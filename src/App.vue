<template>
 <h1> Clicky Game </h1>
 <button @click="start" :disabled="isPlaying"> play </button>
 <Block v-if="isPlaying" :delay="delay" @end="endGame" />
 <ResultsOne v-if="showResults" :score="score" />
</template>

<script>
import Block from './components/Block-one.vue'
import ResultsOne from './components/Results-one.vue'

export default {
    name: 'App',
    components: { Block, ResultsOne },
    data() {
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
        this.isPlaying = true
        this.showResults = false
      },
      endGame(reactionTime) {
        this.score = reactionTime
        this.isPlaying = false
        this.showResults = true
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
  color: #2c3e50;
  margin-top: 60px;
}
button {
  background: blue;
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
