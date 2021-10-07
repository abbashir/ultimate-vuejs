<template>
  <div class="block" v-if="isShowBlock" @click="stopTimer">Click me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      isShowBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.isShowBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style scoped>
.block {
  width: 400px;
  background: crimson;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>