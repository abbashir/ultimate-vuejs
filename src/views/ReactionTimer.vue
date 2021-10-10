<template>
  <h1>Reaction timer game</h1>
  <button @click="start" :disabled="isPlaying" class="btn btn-primary">
    Paly
  </button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />

  <!-- mount here result component -->
  <Result :gameScore="score" v-if="isShowResult" />
</template>

<script>
import Block from "@/components/Block.vue";
import Result from "@/components/Result.vue";
export default {
  components: {
    Block,
    Result,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      isShowResult: false,
    };
  },
  methods: {
    start() {
      this.isShowResult = false;
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.isShowResult = true;
    },
  },
};
</script>

<style>
</style>