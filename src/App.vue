<template>
  <main>
    <aside>
      <SideBar />
    </aside>
    <div class="tracker">
      <TrackerForm @addActivity="addActivity" />
      <div class="list">
        <ActivityContainer v-for="(activity, index) in activities" :key="index" :activity="activity" />  
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SideBar from './components/SideBar.vue';
import TrackerForm from './components/TrackerForm.vue';
import ActivityContainer from './components/ActivityContainer.vue';
import IActivity from './Interfaces/IActivity';

export default defineComponent({
  name: 'App',
  components: {
    SideBar,
    TrackerForm,
    ActivityContainer
  },
  data (){
    return {
      activities: [] as IActivity[]
    }
  },
  methods: {
    addActivity(activity: IActivity){
      this.activities.push(activity);
    }
  }
});
</script>

<style>
 *{
  padding: 0;
  margin: 0;
  border: none;
  box-sizing: border-box;
  text-decoration: none;
  @import url(https://fonts.bunny.net/css);
  font-family: 'Nunito',sans-serif;
 }

 main{
  display: grid;
  grid-template-columns: auto auto auto auto;
 }

 aside{
  width: 100%;
  grid-column: span 1;
 }

 .tracker {
  grid-column: span 3;
  background-color: #FEFEFE;
 }
</style>
