<template>
  <div class="app">
    <div>
      <h1>React Timer</h1>
      <button @click="start" :disabled='isPlaying'>Play</button>
        <ReactionResult v-if='showGameDetails' :score='score'/>
        <div class='cont-div'>
         <Container v-if='isPlaying' :delay='delay' @end='showScore'/>
        </div>
    </div>
 </div>
</template>

<script>
import Container from './components/reactiontimer/Container.vue'
import ReactionResult from './components/reactiontimer/ReactionResult.vue'
export default {
  data() {
    return {
      isPlaying: false,
      score: null,
      delay: null,
      showGameDetails: false
    }
  },

  components: { Container, ReactionResult },

  methods: {
    start() {
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 5
       this.showGameDetails = false
    },
    showScore(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showGameDetails = true
    }
  }
}
</script>
<style>
.app {
  margin:80px 0;
  text-align: center;
  font-family: 'Courier New', Courier, monospace;
  display: flex;
  justify-content:center;
  align-items:center;
}

.cont-div {
  width: 360px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-left: auto;
  margin-right: auto;
}

.app h1 {
  font-weight: bold;
}

.text {
  font-weight: 900;
}

button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 5px;
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