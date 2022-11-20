<script setup>
    import {ref, onMounted, reactive} from 'vue'

    let comments = reactive({data: []});
    let comment = ref("");

    onMounted(() => {
        const apiUrl = "https://lab5-p379.onrender.com/api/v1/messages/";
        fetch(apiUrl)
            .then(response => response.json())
            .then(data => {
                comments.data = data;
        });
    });

    const addComment = () => {
        console.log(comment.value);
    }
</script>

<template>
  <div class="comments">
    <ul>
        <li v-for="comments in comments.data" :key="comments.id">
            <b>{{comments.user}}</b>
            <p>{{comments.text}}</p>
        </li>
    </ul>
  </div>
  <div class="input-field">
    <input type="text" placeholder="Add comment" v-model="comment">
    <button @click="addComment">ADD</button>
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

    .input-field {
        display: flex;
        justify-content: space-between;
        margin: 1rem;
    }
</style>