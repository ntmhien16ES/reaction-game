<template>
  <div class="block" @click="reactionClick">
    <p>Click me</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      reactionTime: 0,
      isClicked: false,
      countTime: null,
    };
  },
  methods: {
    reactionClick() {
      clearInterval(this.countTime);
      this.$emit("endGame", this.reactionTime);
    },
  },
  mounted() {
    this.countTime = setInterval(() => {
      this.reactionTime += 10;
    }, 10);
  },
};
</script>

<style scoped>
.block {
  width: 400px;
  padding: 100px;
  margin: 100px auto;
  background-color: rgb(13, 129, 90);
  color: white;
  border-radius: 10px;
}
</style>