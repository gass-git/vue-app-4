<template>
    <td>
        {{ title }}
    </td>
    <td>
        <img v-bind:src="thumbnail" />
    </td>
</template>

<script setup>
import {defineProps,ref, watchEffect} from 'vue'

    const props = defineProps({ result: Object })
    const title = ref('')
    const thumbnail = ref('')

    watchEffect(() => {
        let data = props.result.snippet

        title.value = data.title
        thumbnail.value = data.thumbnails.medium.url
    })
</script>

<style scope>
    td{
        padding:20px 10px 20px 10px;
        border-bottom: 1px solid rgb(219, 219, 219);
        border-top: 1px solid rgb(219, 219, 219);
    }
    img{
        border-radius:10px;
    }
</style>