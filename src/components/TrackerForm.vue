<template>
  <div class="header">
    <div class="form">
      <div role="form" aria-label="form for create activities"></div>
      <input class="input" type="text" placeholder="Activity Name" v-model=" description" />
    </div>
    <div class="create">
        <TimerTracker @end-timer="endTimer" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TimerTracker from "./TimerTracker.vue";

export default defineComponent({
  name: "TrackerForm",
  emits: ["addActivity"],
  components: {
    TimerTracker,
  },
  data() {
    return {
      description: "",
    };
  },
  methods: {
    endTimer(seconds: number) {
      this.$emit("addActivity", {
        description: this.description,
        seconds,
      })
      this.description = "";
    },
  },
});
</script>

<style>
.header {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  gap: 30px;
  padding: 20px;
 border-bottom: 1px solid #ccc;
 box-shadow: 2px 2px 5px #ccc;
}

.form {
  width: 60%;
}

.input {
  width: 100%;
  padding: 10px 20px 10px 10px ;
  border-radius: 5px;
  border: 1px solid #ccc;
}

.create {
  display: flex;
  align-items: center;
  gap: 20px
}

.buttons {
  display:flex;
  gap: 20px;

}

.button {
  padding: 7px 10px;
  background-color: #fff;
  border: 1px solid #ccc;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 5px;
  cursor: pointer;
  transition: 0.3s;
}

.button:hover {
  background-color: #f0f0f0;
}

.button:focus{
  outline: 1px solid #ccc;
}

</style>
