<template>
  <h1>My Reaction Timer</h1>
  <button @click="start" :disable="playing">Play Game</button>
  <Block v-if="playing" :delay="delay" @end="gameOver"></Block>
  <p v-if="showResults">You scored: {{ score }} sec</p>
</template>

<script>
import Block from './components/Block.vue'


export default {
  name: 'App',

  components: { Block },

  data() {

    return {
      playing: false,
      delay: null,
      score: null,
      showResults: false
    }
  },

  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.playing = true
      this.showResults = false

          },
    gameOver(reactionTime) {
      this.score = reactionTime / 1000
      this.playing = false
      this.showResults = true
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #5d87b1;
  margin-top: 60px;
}
</style>
