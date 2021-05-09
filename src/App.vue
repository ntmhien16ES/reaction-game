<template>
  <div>
    <h1>Reaction game</h1>
    <button class="btn btn-green" @click="startGame" ref="playButton">Play</button>
    <Block v-if="isPlaying" @endGame="endGame"/>
    <Result v-if="showResult" :time="reactionTime"/>
  </div>
</template>

<script>
import Block from "./components/Block";
import Result from "./components/Result";

export default {
  name: "App",
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      reactionTime: null,
      showResult: false,
    };
  },
  methods: {
    startGame() {
      this.$refs.playButton.setAttribute('disabled', true);
      this.delay = 2000 + Math.random()*5000;
      setTimeout(() => {
        this.isPlaying = true;
      }, this.delay);
    },
    endGame(reactionTime) {
      this.isPlaying = false;
      this.reactionTime = reactionTime;
      this.showResult = true;
    }
  },
};
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
.btn {
  padding: 10px 30px;
  color: white;
  border-radius: 10px;
  font-size: 20px;
}
.btn[disabled] {
  opacity: 0.2;
}
.btn-green {
  background-color: rgb(13, 129, 90);
}
</style>
