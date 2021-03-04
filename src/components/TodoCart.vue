<template>
    <div class="bloc">
        <nav>
            <h2 class="date"> {{ date }} </h2>
            <h1><strong> VueJs Tutorial TodoList</strong></h1>
            <h2 class="tache"> {{tasks.length}} Taches</h2>
        </nav>
    <div>
        <new-todo @newTask="submitTask"></new-todo>
        
        <todo-list :tasks="tasks" @finishTask="finish" @poubelleTask="poubelle"></todo-list>

        
    </div>

    </div>
    <!-- <h1> TEST </h1> -->
</template>

<style>
.bloc{
 
    margin: auto;
    background-color: white;
   
}

nav{
    display: flex;
    justify-content: space-between;
    padding: 10px 0;
    box-shadow: 0px 2px 6px grey;
}
.date{
    padding-left: 5%;
}
.tache{
     padding-right: 5%;
}
h1{
    color: #05D3B5;

}
</style>

<script>
import NewTodo from './NewTodo.vue';
import TodoList from './TodoList.vue';
export default {
    
    name: 'todo-cart',
components: {

NewTodo,
TodoList

},
data(){
return {
    tasks: []
}
},
    computed: {
        date: function() {
      let current = new Date();
      let day = current.toLocaleString('default', { weekday: 'long' })
      let month = current.toLocaleString('default', { month: 'long' })
      let date = current.getDate();
      let dateTime = day +' '+ date + ' ' + month ;
      
      return dateTime;
        },

}, 
methods: {
    submitTask(task){
this.tasks.push({description: task, checked:false})
    },
    finish(tache){
        //this.tasks[tache].checked = true
        if(this.tasks[tache].checked === false){
            this.tasks[tache].checked = true
        }
        else{
            this.tasks[tache].checked = false
        }
    },
    poubelle(bellepou){
        this.tasks.splice(bellepou, 1)
    }
}

}
</script>