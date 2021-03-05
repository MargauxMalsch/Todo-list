<template>
<div class="form">
  <input v-model="task" class="input is-primary" type="text" placeholder="Ajouter une tâche">
    <button v-on:click='send' class="button is-success">TRAVAIL</button>
    <button v-on:click='Alltrash' class="button is-danger">ON SUPPRIME TOUS</button>
</div>
</template>
<style scoped>
input{
    width: 30%;
margin: 5% 0px;
border-left: none;
border-bottom: #05D3B5;
}
button{
margin: 5% 10px;
}

</style>

<script>
export default {
    name: 'new-todo',
    data(){
        return {
            task: '',
            }
    },
    methods: {
        send(){
this.$emit('newTask', this.task)
        },
        Alltrash(){
            this.$emit('removeAll')
        }
    }
}
</script>
