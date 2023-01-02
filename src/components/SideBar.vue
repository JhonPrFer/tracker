<template>
  <header>
    <h1>
      Tracker
    </h1>
  </header>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';

  export default defineComponent({
    name: 'SideBar',
  });

</script>
<style>

  header {
    padding: 1rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
  }

  h1 {
      font-size: 1.5rem;
      color: #fff;
  }

  @media only screen and (max-width: 768px) {
    header {
      padding: 2.5rem;
      height: auto;
    }
  }
</style>
