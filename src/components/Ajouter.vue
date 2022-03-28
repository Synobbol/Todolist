<script>
export default {
  props:{
    todoList: Array
  },

  data(){
    return{
      addTask:"Nouvelle tâche",
    }
  },

  methods:{

    createTask(){
      const todo = {
        id: this.todoList.length + 1,
        task:this.addTask,
        done: this.done = false,
      };
      this.todoList.push(todo);
      this.addTask = "";
      console.log(todo);
    },
  },

}
</script>


<template>
  <input type="text" id="task" v-model="addTask">
  <button id="add" type="button" name="notDone" @click="createTask()">Ajouter</button>
    
</template>

<style>

#task{
  color:rgba(46, 52, 82);
}
input{
  width:20%;
  background-color: rgba(255, 216, 164);
  border-radius: 5px;
}

button{
  text-transform: uppercase;
  border-radius: 35px 35px;
  color: #fff;
  padding:0.5em;
  border: none;
  background-color: rgb(231, 161, 69);
  width:10%;
  margin:.5em;
  cursor:pointer;
}
button:hover{
    background-color: rgb(255, 216, 164);
    transition: background-color 1s;
}

#add{
    background-color: rgba(46, 52, 82);
}
#add:hover{
    background-color: rgb(80, 104, 180);
}
</style>