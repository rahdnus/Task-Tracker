<template>
    <div class="container">
        <Header />
        <Tasks @toggle-reminder="toggleReminder"
               @delete-task="deleteTask" 
               :tasks="tasks"/>
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
        this.tasks=[
            {
                id:1,
                text:'DOC',
                day:'March 1',
                reminder:true,
            },
            {
                id:2,
                text:'DOC1',
                day:'March 2',
                reminder:true,
            },
            {
                id:3,
                text:'DOC2',
                day:'March 3',
                reminder:false,
            }
        ]
    },  
    methods:{
        toggleReminder(id)
        {
            this.tasks.map((task)=>{
                if(task.id==id)
                {
                    task.reminder=!task.reminder;
                }
            });
        },
        deleteTask(id)
        {
            this.tasks=this.tasks.filter((task)=>task.id!==id);
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
.container {
  position: fixed;
  top: 50%;
  left: 50%;
  background-color: white;
  transform: translate(-50%, -50%);
  max-width: 500px;
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
