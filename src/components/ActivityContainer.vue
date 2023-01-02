<template>
 <div class="list">
  <div class="container">
    <h1>{{ activity.description }}</h1>
    <TimerMark :seconds="activity.seconds"/>
  </div>
 </div>
</template>


<script lang="ts">
  import { defineComponent, PropType } from 'vue';
  import TimerMark from './TimerMark.vue';
  import IActivity from '../Interfaces/IActivity';

  export default defineComponent({
    name: 'ActivityContainer',
    components: {
      TimerMark,
    },
    props: {
      activity: {
        type: Object as PropType<IActivity>,
        required: true,
      },
    }
  });
  
</script>

<style scoped>
.list {
  display: flex;
  justify-content: center;
  gap: 20px;
  background-color: #fefefe;
  height: 100%;
  width: 100%;
  padding: 5px;

}

.container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #f1f1f1;
  width: 100%;
  height: max-content;
  padding: 10px;
}
</style>