<template>
  <div class="col">
    <button @click="increaseCounter()">{{ counter }}</button>
    <p>{{ goalAchieved }}</p>
    <input type="text" v-model="newtask" />
    <button @click="addTask()">Taak toevoegen</button>
    <p v-if="hasTasks">Alle taken werden uitgevoerd</p>
    <p v-else>Er zijn nieuwe taken beschikbaar</p>
    <ol>
      <li
        v-for="(item, index) in tasks"
        @click="removeTask(index)"
        :key="index"
      >
        {{ item }}
      </li>
    </ol>
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
    hasTasks() {
      if (this.tasks.length == 0) {
        return true;
      } else {
        return false;
      }
    },
  },
  data() {
    return {
      counter: 0,
      JSConfetti: new JSConfetti(),
      tasks: [],
      newtask: "",
    };
  },
  methods: {
    increaseCounter() {
      this.counter++;
    },
    addTask() {
      this.tasks.push(this.newtask);
      this.newtask = "";
    },
    removeTask(index) {
      if (index > -1) {
        this.tasks.splice(index, 1);
      }
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
