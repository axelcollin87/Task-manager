<template>
    <button :style="{ background: color }" @click="$emit('add-task-clicked')">
        {{ text }}
    </button>
</template>

<script>
export default {
    name: "Button",
    props: {
        text: String,
        color: String,
    },
    emits: ["add-task-clicked"],
};
</script>

<style scoped>
button {
    font-size: 1.5em;
    color: white;
    border: 1px solid white;
    border-radius: 5px;
    cursor: pointer;
    padding: 10px;
    margin: 10px;
    width: 95%;
}
</style>
