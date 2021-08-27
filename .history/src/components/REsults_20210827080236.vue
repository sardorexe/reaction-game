<template>
  <p class="result">
    Your reaction time is: <span>{{ score }}</span> ms
  </p>
  <p class="message">{{ rank }}</p>
</template>

<script>
export default {
  name: "Results",
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Wow! Amazing fingers";
    } else if (this.score < 300) {
      this.rank = "Great reaction!";
    } else if (this.score < 400) {
      this.rank = "Weak reaction.";
    } else {
      this.rank = "Ah shit, here you'll go again!";
    }
  },
};
</script>

<style scoped>
.result {
  margin: 8px;
  font-size: 13px;
  color: rgba(51, 51, 51, 0.616);
}

.result span {
  font-weight: 700;
}

.message {
  font-size: 20px;
  font-weight: 700;
}
</style>