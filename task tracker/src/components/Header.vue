<template>
    <header>
        <h1>TASK TRACKER</h1>
        <Button @toggleshow="toggle" v-show="!showform" text="ADD" color="green" />
        <div v-show="showform">
            <form @submit="onSubmit" class="add-form">
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
            <input @click="toggle" type="submit" value="Cancel" class="btn btn-block" style="background:red" />
        </form>
        </div>
    </header>
</template>

<script>
import Button from "./Button.vue"
export default {
    name: "Header",
    components: { Button },
    data(){
        return {
            showform:false
        }
    },
    methods:{
        toggle()
        {
            this.showform=!this.showform;
        },
        onSubmit(e)
        {
            e.preventDefault();
        }
    }
}
</script>

<style scoped>
header {
    /* border-radius: 5px;
    justify-content: space-between;
    display: flex;
    align-items: center; */
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
