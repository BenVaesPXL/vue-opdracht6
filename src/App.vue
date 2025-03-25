<template>
  <div class="col">
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
<style>
.col {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  width: 25%;
  margin: 0 auto;
  border: 1px solid black;
  padding: 2rem;
}
</style>
