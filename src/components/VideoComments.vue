<script setup>
    import {ref, onMounted} from 'vue'

    let user = "Marie"
</script>

<template>
  <div class="comments">
    <b>{{user}}</b>
  </div>

</template>

<style scoped>
    .comments {
        padding: 1rem;
    }
</style>