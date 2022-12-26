<template>
    <div class="container">
        <Header @add-task="addTask" />
        <div class="tasks">
            <Tasks @toggle-reminder="toggleReminder"
               @delete-task="deleteTask" 
               :tasks="tasks"/>
        </div>
   
    </div>
</template>

<script>
import Header from "./components/Header.vue"
import Tasks from "./components/Tasks.vue"


export default {
    data()
    {
        return{
            tasks:[],
        }
    },
  
    created()
    {
        const newtask=JSON.parse(localStorage.getItem('tasks'));
        this.tasks=!newtask||newtask.length == 0?[{ text: "Add a New Task!",
            day: "Today",
            reminder: false}]:newtask;
    
     
    },  
    methods:{
        addTask(newtask)
        {
            this.tasks=this.tasks?[...this.tasks,newtask]:[newtask];
            localStorage.setItem('tasks',JSON.stringify(this.tasks))
        },
        toggleReminder(id)
        {
            this.tasks.map((task)=>{
                if(task.id==id)
                {
                    task.reminder=!task.reminder;
                }
            });
            localStorage.setItem('tasks',JSON.stringify(this.tasks))

        },
        deleteTask(id)
        {
            this.tasks=this.tasks.filter((task)=>task.id!==id);
            localStorage.setItem('tasks',JSON.stringify(this.tasks))
        }   
    }
    ,
    name: "App",
    components: {Header,Tasks},
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.tasks{
  overflow: auto;
  max-height: 300px;
}
.container {
  position: fixed;
  top: 50%;
  left: 50%;
  background-color: white;
  transform: translate(-50%, -50%);
  min-width: 500px;

  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
    
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
