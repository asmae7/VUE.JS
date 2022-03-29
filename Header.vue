<template>
   <header>
       <h1>
         {{title}}
       </h1>
       <Button @toggle-add-task="$emit('toggle-add-task')" :text=" showAddTask ? 'Fermer'  : 'Ajouter une tâche'" color="black"/>
       
       </header> 
</template>
<script>
import Button from "./Button"

export default {
    name:"header",
    props:{
        title:String,
        showAddTask:Boolean
    },
    components:{
        Button
    }
}
 

</script>
<style scoped>
  Header{
      display:flex ;
       justify-content: space-between;
       align-items: center;
       margin-bottom: 20px;
  }
</style>
