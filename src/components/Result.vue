<template>
  <p>Reaction time: {{ gameScore }} ms, is it right?</p>
  <p>{{ rank }}</p>
</template>

<script>
export default {
  props: ["gameScore"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.gameScore < 400) {
      this.rank = "Bagher bacca...";
    } else if (this.gameScore < 500) {
      this.rank = "Expert...";
    }else{
        this.rank = "Tomake diye game hobe na..."
    }
  },
};
</script>

<style>
</style>