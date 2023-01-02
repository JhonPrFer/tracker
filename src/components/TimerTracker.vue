<template>
  <section class="timer">
    <TimerMark :seconds="seconds" />
    <div class="buttons">
      <button class="button" @click="start" :disabled="running">
        <span class="icon">
          <i class="fas fa-play"></i>
        </span>
        <span>Play</span>
      </button>
      <button class="button" @click="stop" :disabled="!running">
        <span class="icon">
          <i class="fas fa-stop"></i>
        </span>
        <span>Stop</span>
      </button>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TimerMark from "./TimerMark.vue";
export default defineComponent({
  name: "TimerTracker",
  emits: ["endTimer"],
  components: {
    TimerMark,
  },
  data() {
    return {
      seconds: 0,
      timer: 0,
      running: false,
    };
  },
  methods: {
    start() {
      this.running = true;
      this.timer = setInterval(() => {
        this.seconds++;
      }, 1000);
    },
    stop() {
      this.running = false;
      clearInterval(this.timer);
      this.$emit("endTimer", this.seconds);
      this.seconds = 0;
    },
  },
});
</script>

<style>
  .timer {
    display: flex; 
    align-items: center;
    justify-content: center;
    gap: 1.25rem;
  }
</style>