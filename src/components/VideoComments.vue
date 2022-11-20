<script setup>
    import {ref, onMounted} from 'vue'

    let user = ref("");
    let text = "test text";

    onMounted(() => {
        const apiUrl = "https://lab5-p379.onrender.com/api/v1/messages/";
        fetch(apiUrl)
            .then(response => response.json())
            .then(data => {
                user.value = data[0].user;
        });
    })
</script>

<template>
  <div class="comments">
    <b>{{user}}</b>
    <p>{{text}}</p>
  </div>

</template>

<style scoped>
    .comments {
        padding: 1rem;
    }
</style>