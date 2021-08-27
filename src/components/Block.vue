<template>
  <div @click="stopTimer" v-if="showBlock" class="block">HURRY UP!</div>
</template>

<style scoped>
.block {
  width: 70%;
  height: 300px;
  background: #42b883;
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #fff;
  margin-top: 20px;
  cursor: pointer;
}
</style>

<script>
export default {
  name: "Block",
  props: ["delay"],

  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTimer: 0,
    };
  },

  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },

  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTimer += 10;
      }, 10);
    },

    stopTimer() {
      this.showBlock = false
      clearInterval(this.timer);
      this.$emit("end", this.reactionTimer)
    },
  },
};
</script>