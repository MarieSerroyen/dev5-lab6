<script setup>
    import {ref, onMounted} from 'vue'
    
    let username = ref("")
    let description = ref("")

    onMounted(() => {
        const apiUrl = "https://app.fakejson.com/q/ipsgR0e0?token=dpQ9m4it4XS-5oTmIu1YlQ";
        fetch(apiUrl)
            .then(response => response.json())
            .then(data => {
                username.value = data.videos[0].username;
                description.value = data.videos[0].description;
        });
    })
</script>

<template>
  <div class="details">
    <h3>{{username}}</h3>
    <p>{{description}}</p>
  </div>

</template>

<style scoped>
    .details {
        padding: 1rem;
    }
</style>