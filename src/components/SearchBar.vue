<template>
    <section id="search-bar-container">
        <div id="grid-box">
            <input @input="$emit('updateInputText', $event)" />
            <button @click="$emit('handleSubmit')">search</button>
        </div>
    </section>    
</template>

<script setup>

</script>

<style scoped>
    #search-bar-container{
        display: grid;
        place-items: center;
        width:80vw;
        max-width: 600px;
        min-width: 400px;
        padding:20px;
        border-radius:10px;
        background:#e9e9e9;
        border:1px solid #d8d8d8;
    }
    #grid-box{
        display: flex;
        justify-content: center;
        width:90%;
    }
    #grid-box > * {
        font-size:17px;
        border-radius:5px;
        border:0;
    }
    input{
        width:300px;
        padding:0 10px 0 10px;
    }
    button{
        margin: 0 0 0 10px;
        padding:5px 10px 5px 10px;
        background: rgb(84, 84, 84);
        color:white;
        cursor: pointer;
    }
    button:hover{
        background: rgb(115, 115, 115);
    }
    button:active{
        background: rgb(147, 147, 147);
    }
</style>