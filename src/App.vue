<script setup>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
</script>

<script>
  export default {
    data() {
      return {
        isPlaying: false,
        delay: null,
        score: null,
        showResults: false
      }
    },
    methods: {
      startGame() {
        // console.log('clicked start'),
        this.delay = 2000 + Math.random() * 5000,
        this.isPlaying = true
        this.showResults = false
        // console.log(this.delay)
      },
      endGame(reactionTime) {
        this.score = reactionTime
        this.isPlaying = false
        this.showResults = true
      }
    }
  }
</script>

<template>
  <h1>Reaction Timer</h1>
  <br>
  <button @click="startGame" :disabled="isPlaying">Start Game</button>
  <br>
  <Block v-if="isPlaying" :delay="delay" @endGame="endGame" />
  <Results v-if="showResults" :score="score" />
  <!-- <p v-if="showResults">reaction time = {{ score }} ms</p> -->
</template>

<style>
/* header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
} */

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
