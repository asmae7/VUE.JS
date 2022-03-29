<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Suivi des tâches" :showAddTask="showAddTask" />
    <div v-show="showAddTask">
<AddTask @add-task="addTask" />
    </div>
    <Tasks @toggle-reminder="toggleReminder"
     @delete-task="deleteTask" :tasks="tasks" />
     <Footer/>

  </div>
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'
import Footer from './components/Footer'
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
    Footer,
  },
  data() {
    return {
      tasks:[],
      showAddTask:false,
    }
  },
  created(){
    this.tasks=[
      {
        id:1,
        text:"rendez-vous chez le docteur",
        day:"le 21 Mars à 12h30",
        reminder:true,
      },
       {
        id:2,
        text:"télé-travail",
        day:"le 23 Avril à 10h35",
        reminder:false,
      },
       {
        id:3,
        text:"rendez-vous chez le dentiste",
        day:"le 21 Mars à 15h30",
        reminder:true,
      },
       {
        id:4,
        text:"Réunion à l'école",
        day:"le 25 Mars à 14h30",
        reminder:true,
      },
    ]
  },
  methods: {
    deleteTask(id){
      if(confirm("vous êtes sûr?")){
this.tasks=this.tasks.filter((task) => task.id !== id )
    }
     },
  toggleReminder(id){
this.tasks=this.tasks.map((task) => task.id===id ? {...task, reminder: !task.reminder} : task
)
  },
  addTask(task){
    this.tasks=[...this.tasks,task]
  },
  toggleAddTask(){
    this.showAddTask=!this.showAddTask
  },
},
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
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid rgb(35, 1, 39);
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: rgb(29, 1, 29);
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
