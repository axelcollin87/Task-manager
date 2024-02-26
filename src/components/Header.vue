<template>
    <header>
        <h1 :style="{color: color}">{{text}}</h1> 
    </header>
</template>

<script >
    export default {
        name: 'Header',
        props: {
            text: String,
            color: String
        }
    }   
</script>

<style scoped>
    h1 {
        font-size: 3em;
    }
</style>