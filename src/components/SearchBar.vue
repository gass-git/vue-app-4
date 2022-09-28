<template>
    <div>
        <input @input="$emit('updateInputText', $event)" />
        <button @click="$emit('handleSubmit')">search</button>
    </div>    
</template>

<script setup>


</script>

<style scoped>
    
</style>