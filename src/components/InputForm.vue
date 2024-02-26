<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label for="task">Task</label>
            <input
                v-model:="task"
                type="text"
                name="task"
                placeholder="Add Task" />
        </div>
        <div class="form-control">
            <label for="desc">Description</label>
            <input
                v-model:="desc"
                type="text"
                name="desc"
                placeholder="Add Description" />
        </div>
        <div class="form-control form-control-check">
            <label for="reminder">Set Reminder</label>
            <input v-model:="reminder" type="checkbox" name="reminder" />
        </div>
        <input type="submit" value="Save Task" class="btn btn-block" />
    </form>
</template>

<script>
export default {
    name: "InputForm",

    data() {
        return {
            task: "",
            desc: "",
            reminder: false,
        };
    },

    methods: {
        onSubmit(e) {
            e.preventDefault();

            if (!this.task) {
                alert("Please type something");
                return;
            }

            const newTask = {
                id: Math.floor(Math.random() * 100000),
                task: this.task,
                desc: this.desc,
                reminder: this.reminder,
            };

            this.$emit("task-added", newTask);

            this.task = "";
            this.desc = "";
            this.reminder = false;
        },
    },
};
</script>

<style scoped>
.add-form {
    margin: 20px 0;
}
.add-form .form-control {
    margin-bottom: 10px;
}
.add-form .form-control label {
    display: block;
}
.add-form .form-control input {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
}
.add-form .form-control-check {
    display: flex;
    align-items: center;
}
.add-form .form-control-check label {
    margin: 0;
}
.add-form .form-control-check input {
    margin: 0 10px 0 0;
}
.add-form .btn {
    width: 100%;
    background: #333;
    color: #fff;
    border: none;
    padding: 10px;
    cursor: pointer;
}
.add-form .btn:hover {
    background: #416841;
}
</style>
