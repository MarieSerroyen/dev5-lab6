<script setup>
    import {ref, onMounted, reactive} from 'vue'

    let comments = reactive({data: []});

    onMounted(() => {
        const apiUrl = "https://lab5-p379.onrender.com/api/v1/messages/";
        fetch(apiUrl)
            .then(response => response.json())
            .then(data => {
                comments.data = data;
        });
    })
</script>

<template>
  <div class="comments">
    <ul>
        <li v-for="comments in comments.data" :key="comments.id">
            <b>{{comments.user}}</b>
            <p>{{comments.text}}</p>
        </li>
    </ul>
    <div>
        <input type="text" placeholder="Add comment">
        <button>ADD</button>
    </div>
  </div>

</template>

<style scoped>
    .comments {
        margin-left: 1rem;
        width: 100;
        height: 70vh;
        overflow: scroll;
        border: 1px solid blue;
    }

    li {
        list-style: none;
    }
</style>