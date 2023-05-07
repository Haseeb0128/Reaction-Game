<template>
  <div class="container">
    <h1>Reaction Time Game</h1>
    <button :disabled="isPlaying" @click="startGame">Play</button>
    <Results v-if="showResults" :score="score" />
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  </div>
</template>

<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue';

export default {
  name: 'App',
  components: {
    Block,
    Results,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods: {
    // The start game function keeps track if the user is playing the game.
    // It also sets the delay for the clickable block/circle or object to appear on the screen. 
    startGame() {
      this.delay = 2000 + Math.random() * 6000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      // The reaction time is the score
      this.score = reactionTime;
      // The game will end.
      this.isPlaying = false;
      this.showResults = true;
    },
  }
}
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

button {
  width: 100px;
  height: 50px;
  font-size: 20px;
  border-radius: 15px;
  background: green;
  color: white;
  border: none;
  cursor: pointer;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>