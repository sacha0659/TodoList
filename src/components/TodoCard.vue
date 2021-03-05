<template>
    <div id="TodoCard">
        <nav>
            <p>{{date}}</p>
            <h1>{{msg}} </h1>
            <p>{{tasks.length}} taches</p>
        </nav>
        <main>
            <NewTodo @addTask="viewnewtask" />
            <!-- Pour chaque element du tableau, j'affiche le composent TodoList -->
            <div v-for="task in tasks" :key="task.id">
                <TodoList :name="task.name"/>
            </div>
        </main>
    </div>
</template>

<script>
import  NewTodo from "./NewTodo";
import  TodoList from "./TodoList";
export default {
    data() {
        return {
            msg: 'VueJs Tutorial ToDo List',
            tasks:[]
        }
    },
    // Cette fonction calcule et affiche la date en lettres
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

     components: {
    NewTodo,
    TodoList,
  },
  //Cette methode ajoute la task dans le tableau tasks
  methods: {
      viewnewtask(task){
          this.tasks.push({name: task});
      }
  }

}

</script>

<style scoped>
#TodoCard{
    width: 50%;
    height: 50vh;
    background-color: rgb(255, 255, 255);
    border-radius: 15px;
    margin: 0 auto;

}
nav{
    display: flex;
    justify-content: space-around;
    background-color: white;
    border-top-left-radius: 15px;
    border-top-right-radius: 15px;  
    /* justify-content: center; */
    padding: 15px;
    box-shadow: rgba(71, 71, 71, 0.212) 0px 6px 12px ;
}
h1{
    color: rgb(21, 226, 158);
    font-weight: bolder;
}
</style>