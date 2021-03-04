<template>
    <h1>TODO</h1>
    <ul v-for="(task, index) in tasks" :key="(task, index)">
        <li v-bind:class="{'ok':task.checked}">{{task.description}}</li>
         <input type="checkbox" v-on:click='changement(index)'>
         <button v-on:click='poubelle(index)'>POUBELLE</button>
    </ul>
</template>
<style scoped>
ul{
    display: flex;
    justify-content: center;
}
.ok{
    color:blue
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