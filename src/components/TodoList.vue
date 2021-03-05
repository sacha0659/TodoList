<template>
    <div id="TodoList" >
        <input v-model="checked" type="checkbox"/>
        <p  v-bind:class= "{checked: checked}">{{name}} </p>
        <button v-on:click="trash">Delete</button>
       
    </div>
</template>

<script>
export default {
    props:{
        name: String,
        },
        //essai de suppression que je n'ai pas réussi 
    methods:{
        trash(index){
            console.log(index);
            this.$emit('deleteTask',index)
        }
    },
    data(){
        return{
            checked: false

        }
    }
}
</script>

<style scoped>
#TodoList{
    display: flex;
    width: 80%;
    margin: auto;
    justify-content: space-around;
    
}
.checked{
    text-decoration:line-through;
    color:green
}

</style>
