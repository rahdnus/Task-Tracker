<template>
    <header>
        <h1 class="center"><b>TASK TRACKER</b></h1>
        <Button @toggleshow="toggle" v-show="!showform" text="NEW" color="green" />
        <div v-show="showform" class="add-form">
            <form @submit="onSubmit" >
                <div class="form-control">
                    <label>Task</label>
                    <input type="text" v-model="text" name="text" placeholder="Add Task" />
                </div>
                <div class="form-control">
                    <label>Day & Time</label>
                    <input type="text" v-model="day" name="day" placeholder="Add Day & Time" />
                </div>
                <div class="form-control form-control-check">
                    <label>Set Reminder</label>
                    <input type="checkbox" v-model="reminder" name="reminder" />
                </div>
                <input type="submit" value="Save Task" class="btn btn-block" />
            </form>
            <button @click="toggle" class="btn btn-block" style="background:red" >Cancel</button>
        </div>
    </header>
</template>

<script>
import Button from "./Button.vue"
export default {
    name: "Header",
    components: { Button },
    data() {
        return {
            showform: false,
            text: "",
            day: "",
            reminder: false
        }
    },
    emits:['add-task'],
    methods: {
        toggle() {
            this.showform = !this.showform;
        },
        onSubmit(e) {
            e.preventDefault();
           
            if (!this.text) {
                alert('Please add a task')
                return
            }
            const newTask = {
                id: Math.floor(Math.random() * 100000),
                text: this.text,
                day: this.day,
                reminder: this.reminder,
            }
            this.$emit('add-task', newTask)
            this.text = ''
            this.day = ''
            this.reminder = false
        }
    }
}
</script>

<style scoped>
.center {
    display: flex;
    justify-content: center;
    align-items: center;
}

header {
    background-color: aliceblue;
    color: black;
}

.add-form {
    margin-bottom: 40px;
}

.form-control {
    margin: 20px 0;
}

.form-control label {
    display: block;
}

.form-control input {
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
}

.form-control-check {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.form-control-check label {
    flex: 1;
}

.form-control-check input {
    flex: 2;
    height: 20px;
}
</style>
