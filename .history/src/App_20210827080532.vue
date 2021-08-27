<template>
  <div class="game">
    <h1 class="title">Reaction Game</h1>
    <span class="span">with vuejs</span>
    <button :disabled="clicked" @click="setClick" class="btn">Click</button>
    <Block @end="endGame" v-if="clicked" :delay="delay" />
    <Results :score="score" v-if="showResults" />
  </div>
</template>

<script>
import Results from "./components/Results.vue";
import Block from "./components/Block.vue";

export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
      clicked: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    setClick() {
      this.clicked = true;
      this.delay = 200 + Math.floor(Math.random() * 5000);
      this.showResults = false;
    },

    endGame(reactionTimer) {
      this.clicked = false
      this.score = reactionTimer;
      this.showResults = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #333;
}

.title {
  margin-bottom: 5px;
  color: #42b883;
  font-weight: 800;
}

.span {
  font-family: sans-serif;
  font-size: 12px;
  text-transform: uppercase;
  opacity: 0.5;
  font-weight: 600;
}

.game {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.btn {
  margin-top: 10px;
  background: #42b883;
  border: none;
  color: #fff;
  border-radius: 2px;
  cursor: pointer;
  padding: 10px 25px;
  transition: all 0.3 ease-in;
}

.btn:disabled {
  background: #ccc;
  color: #333;
  cursor: not-allowed;
  opacity: 0.5;
  transition: all 0.3 ease-in;
}


</style>
