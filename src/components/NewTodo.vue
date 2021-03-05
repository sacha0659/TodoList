<template>
<div id="NewTodo">
    <input v-model="newTask" type="text">
    <button v-on:click="sendTask">+</button>
    
</div>
</template>

<script>
export default {
    data(){
        return{
            newTask: null,
            
        }
    },
    //Cette methode verifie que la variable n'est pas nulle mais également > a 3 caracteres.
    methods:{
        sendTask(){
            if(this.newTask !== null && this.newTask.length >= 3){
                
                this.$emit('addTask',this.newTask);
            }
        }
    }
    
}
</script>

<style scoped>
#NewTodo{
    margin: 15px auto;
    width:40%;
}
input{
    width:90%;
    padding: 15px;
    
}
</style>
