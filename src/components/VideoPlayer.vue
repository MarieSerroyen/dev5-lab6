<script setup>
    import {ref, onMounted, reactive} from 'vue'
    import 'animate.css'

    let videos = reactive({data: []})
    let videoSrc = ref("")
    let counter = ref(0)
    let animation = ref("")

    //onMounted bij load van de pagina
    onMounted(() => {
        const apiUrl = "https://app.fakejson.com/q/ipsgR0e0?token=dpQ9m4it4XS-5oTmIu1YlQ";
        fetch(apiUrl)
            .then(response => response.json())
            .then(data => {
                videos.data = data.videos;
                videoSrc.value = data.videos[0].video;
        });
    });

    const nextVideo = () => {
        animation.value = "animate__slideInUp";
        counter.value++;
        videoSrc.value = videos.data[counter.value].video;        
    }
</script>

<template>
  <div class="blur">
    <div class="controls">
        <a @click.prevent="nextVideo" href="#">⬇</a>
        <!--<a href="#">⬆</a>   -->     
    </div>
    <video 
    :src="videoSrc"
    :class="animation"
    class="animate__animated"
    autoplay
    muted
    ></video>
  </div>

</template>

<style scoped>
    video {
        max-width: 100%;
        max-height: 100vh;
    }
    .blur {
        background-image: url("/blur-photo.jpg");
        background-size: cover;
        text-align: center;
        position: relative;
    }

    .controls {
        position: absolute;
        top: 0;
        right: 0;
        height: 100%;
        display: flex;
        align-items: center;
    } 

    .controls a {
        color : white;
        text-decoration: none;
        font-size: 2em;
        padding: 1rem;
    }
</style>
