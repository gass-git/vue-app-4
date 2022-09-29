<script setup>
    import {defineProps, watchEffect, ref} from 'vue'

    const props = defineProps({selectedVideoId: String})
    const videoUrl = ref('')

    watchEffect(() => {
        if(props.selectedVideoId !== ''){
            videoUrl.value = 'https://www.youtube.com/embed/' + props.selectedVideoId
        }
    })
</script>

<template>
    <section id="video-container">
        <iframe v-if="videoUrl !== ''" width="500" height="270" v-bind:src="videoUrl">
        </iframe>
        <div v-else id="no-video">
            <h1>
               👉 no video has been selected yet
            </h1>
        </div>
    </section>    
</template>

<style scoped>
    #video-container{
        margin:30px 0 0 0;
        width:640px;
        height: 300px;
        display: grid;
        place-items: center;
        background:#e9e9e9;
        border-radius: 10px;
        border:1px solid #d8d8d8;
    }
    #no-video{
        width:500px;
        height: 270px;
        display: grid;
        place-items:center;
        background: black;
    }
    h1{
        font-size:25px;
        color:white;
    }
</style>
