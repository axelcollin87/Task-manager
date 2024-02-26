<template>
    <div class="container">
        <Header color="White" text="ToDoListGG" />
        <Tasks
            @toggle-reminder="toggleReminder"
            @delete-task="deleteTask"
            :tasks="tasks" />
        <Button
            :showAddTasks="showAddTasks"
            @add-task-clicked="showAddForm"
            :text="showAddTasks ? 'Cancel input' : 'Add new task'"
            :color="showAddTasks ? '#FF453A' : '#00C853'" />

        <div v-show:="showAddTasks">
            <InputForm @task-added="addNewTask" />
        </div>
    </div>
</template>

<script>
function deleteTask(id) {
    this.tasks = this.tasks.filter((task) => task.id !== id);
}

import Header from "./components/Header.vue";
import Button from "./components/Button.vue";
import Tasks from "./components/Tasks.vue";
import InputForm from "./components/InputForm.vue";

export default {
    name: "App",
    components: {
        Header,
        Button,
        Tasks,
        InputForm,
    },

    data() {
        return {
            tasks: [],
            showAddTasks: false,
        };
    },

    methods: {
        deleteTask(id) {
            this.tasks = this.tasks.filter((task) => task.id !== id);
        },
        toggleReminder(id) {
            this.tasks = this.tasks.map((task) =>
                task.id === id ? { ...task, reminder: !task.reminder } : task
            );
        },
        addNewTask(task) {
            this.tasks.push(task);
        },
        showAddForm() {
            this.showAddTasks = !this.showAddTasks;
        },
    },

    created() {
        this.tasks = [
            {
                id: 1,
                task: "",
                desc: "Spring 20km, @5min/km",
                reminder: true,
            },
            {
                id: 2,
                task: "Städa",
                desc: "Städa allt, du är ful.",
                reminder: false,
            },
            { id: 3, task: "Bajsa", desc: "Det är dags nu!", reminder: true },
            {
                id: 4,
                task: "Tandläkare",
                desc: "Hål hål hål!",
                reminder: true,
            },
            { id: 5, task: "Börja om", desc: "Från början!", reminder: true },
        ];
    },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;500;700&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap");

* {
    font-family: "Open Sans", sans-serif;
    font-weight: 500;
}

.container {
    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>
