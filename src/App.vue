<template>
  <div>
    <button @click="increaseCounter()">{{ counter }}</button>
    <p>{{ goalAchieved }}</p>
  </div>
</template>
<script>
import JSConfetti from "js-confetti";
import { computed } from "vue";

export default {
  computed: {
    goalAchieved() {
      if (this.counter >= 10) {
        this.JSConfetti.addConfetti();
        return "Doel bereikt";
      } else {
        return "klik nog meer";
      }
    },
  },
  data() {
    return {
      counter: 0,
      JSConfetti: new JSConfetti(),
    };
  },
  methods: {
    increaseCounter() {
      this.counter++;
    },
  },
};
</script>
<style></style>
