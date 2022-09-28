<script setup>
import {defineProps} from 'vue'
import VideoListItem from './VideoListItem.vue'

    const props = defineProps({results: Array})
</script>

<template>
    <table v-if="results.length > 0">
        <tr v-for="result in props.results" 
            v-bind:key="result.id.videoId"
        >
            <VideoListItem v-bind:result="result" />
        </tr>
    </table>
</template>

<style scoped>
    table{
        margin-top: 20px;
        border:1px solid black;
    }
    td{
        border:1px solid grey;
        padding:5px 15px 5px 15px;
    }
</style>