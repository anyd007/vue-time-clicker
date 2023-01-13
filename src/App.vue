<template>
  <h1>SPRAWDŹ SWÓJ REFLEKS</h1>
  <button class="start-game-btn" @click="start" :disabled="isPlaying">START</button>
  <Result v-if="showScore" :score="score"/>
  <Block v-if="isPlaying" :delay="dalay" @end="endGame"/>
</template>

<script>
import Block  from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  
  components: { Block, Result },

  data(){
    return {
      isPlaying: false,
      dalay: null,
      score: null,
      showScore: false
    }
  },

  methods: {
    start() {
      this.dalay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showScore = false
    },

    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showScore = true
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
.start-game-btn{
  cursor: pointer;
  padding: 30px;
  border-radius: 10px;
  font-size: 20px;
  border: none;
  background: tomato;
  color: #fff;
  background-image: linear-gradient(
    to right, 
    rgba(0,0,0,0.4), rgba(0,0,0,0.1));
    box-shadow: inset 0 0 0 transparent, 2px 3px 40px 5px #000;
}
.start-game-btn[disabled]{
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
