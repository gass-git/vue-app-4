<script setup>
    import axios from 'axios'
    import {ref} from 'vue'
    import SearchBar from './components/SearchBar.vue'
    import VideoList from './components/VideoList.vue'

    const API_KEY = 'AIzaSyDXQ4C8gbVIJi5rIp1nlQZAR3BHsE6LbTI'
    const API_URL = 'https://www.googleapis.com/youtube/v3/search'
    const inputText = ref('')
    const results = ref([])

    function updateInputText(e){
        inputText.value = e.target.value
    }

    function handleSubmit(){
        if(inputText.value !== '') fetchYoutubeData()
        else results.value = []
    }

    function fetchYoutubeData(){    
        axios.get(API_URL, {
            params:{
                key: API_KEY,
                type: 'video',
                part: 'snippet',
                q: inputText.value
            }
        }).then((resp) => {
            results.value = resp.data.items
        }).catch((error) => {
            return console.log(error)
        });
    }
</script>

<template>
    <section id="main-container">
        <SearchBar 
            @updateInputText="updateInputText"
            @handleSubmit="handleSubmit"
        />
        <VideoList v-bind:results="results" />
    </section>
</template>

<style>
    #main-container{
        margin:30px 0 0 0;
        width:100vw;
        display:grid;
        justify-content: center;
        grid-template-columns: auto;
    }
</style>
