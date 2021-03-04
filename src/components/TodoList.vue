<template>
    <h1>TODO</h1>
    <ul v-for="(task, index) in tasks" :key="(task, index)">
         <input type="checkbox" v-on:click='changement(index)'>

        <li v-bind:class="{'ok':task.checked}">{{task.description}}</li>
        
         <button v-on:click='poubelle(index)' class="button is-danger is-light">POUBELLE</button>
    </ul>
</template>
<style scoped>
ul{
    display: flex;
    justify-content: center;
    padding: 7px;
}
li{
    display: flex;
 align-items: center;
 padding: 0 2%;
 font-size: 2em;
}
button{
    margin: 3%;
}

.ok{
    color:palevioletred;
    text-decoration: line-through;
}


</style>

<script>
export default {
    name: 'todo-list',
    props: ['tasks'],
    methods: {
        changement(index){
this.$emit('finishTask', index)
        },
        poubelle(index){
            this.$emit('poubelleTask' , index)
        }
    }
}
</script>