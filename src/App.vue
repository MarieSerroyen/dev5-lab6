<script setup>
  import VideoPlayer from './components/VideoPlayer.vue'
  import VideoDetails from './components/VideoDetails.vue'
  import VideoComments from './components/VideoComments.vue'
</script>

<template>
  <div class="app">
    <VideoPlayer/>
    <div class="info">
      <VideoDetails/>
      <VideoComments/>
    </div>    
  </div>
</template>

<style scoped>
  .app {
    display: grid;
    grid-template-columns: 6fr 4fr;
  }
</style>
