<script setup>
    import {defineProps} from 'vue'
    import VideoListItem from './VideoListItem.vue'

    const props = defineProps({results: Array})
</script>

<template>
    <table v-if="results.length > 0">
        <tr v-for="result in props.results" 
            v-bind:key="result.id.videoId"
            @click="$emit('handleSelection', result.id.videoId)"
        >
            <VideoListItem v-bind:result="result" />
        </tr>
    </table>
</template>

<style scoped>
    table{
        border-collapse: collapse;
        width:100vw;
        max-width: 640px;
        min-width: 300px;
        margin:30px 0 50px 0; 
    }
    tr:hover{
        cursor:pointer;
        background:#f1f1f1;
    }
</style>