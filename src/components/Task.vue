<template>
    <div
        @dblclick="$emit('toggle-reminder', task.id)"
        :class="[task.reminder ? 'reminder' : '']">
        <h3>
            {{ task.task }}
            <i
                @click="$emit('delete-task', task.id)"
                class="fas fa-times-circle"></i>
        </h3>
        <p>{{ task.desc }}</p>
    </div>
</template>

<script>
export default {
    name: "Task",
    props: {
        task: Object,
    },
    emits: ["delete-task", "toggle-reminder"],
};
</script>

<style scoped>
div {
    padding: 10px;
    margin: 3px;
    border: 4px solid transparent;
    width: 400px;
    background-color: rgb(31, 31, 31);
}

.fas {
    color: red;
}

.fas:hover {
    cursor: pointer;
}

h3 {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 25px;
    color: #ffffff;
}

p {
    font-size: 14px;
    color: white;
}

.reminder {
    border-left: 4px solid #00c853;
    border-right: 4px solid #00c853;
}
</style>
