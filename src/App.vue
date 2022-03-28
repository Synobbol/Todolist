<script>
// import { RouterLink, RouterView } from 'vue-router'
// import HelloWorld from '@/components/HelloWorld.vue'
import Modifier from '@/components/Modifier.vue';
import Ajouter from '@/components/Ajouter.vue'
import Supprimer from "@/components/Supprimer.vue"

export default {
  components: { /*RouterLink, RouterView, HelloWorld,*/ Ajouter, Supprimer, Modifier },

  data (){
    return{
      message: "To-do list",
      message1:"Tâches à faire:",
      message2:"Tâches faites:", 

      todoList:[
        {id: 0, task: "Faire les courses", done: false},
        {id: 1, task: "Faire la vaisselle", done: false},
        {id: 2, task: "Passer l'aspi", done: true},
        {id: 3, task: "Ranger", done: false},
        {id: 4, task: "Faire les comptes", done: true},
        {id: 5, task: "Répondre aux mails", done: true},
      ],

    }
  },
  
  computed: {
    taskDone() {
       return this.todoList.filter(task => task.done);
    },
    taskNotDone() {
      return this.todoList.filter(task => !task.done);
    },
  },

}
</script>


<template>
  <header>
    <!-- <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" /> -->

    <div class="wrapper">
      <!-- <HelloWorld msg="You did it!" /> -->
      <h1>{{ message }}</h1>
      <section class="nDone">
        <h2>{{ message1 }}</h2>
          <ul>
              <li v-for="task in taskNotDone" :key="id" class="liste">

                <Supprimer v-bind:id="task.id" v-bind:todoList="todoList" />

                {{ task.task }}
                <button type="button" name="done" @click="task.done = !task.done">Fait</button>

                <Modifier v-bind:id="task.id" v-bind:todoList="todoList" />

              </li>
          </ul>
          
          <Ajouter  :todoList="todoList" />

      </section>

      <section class="done">
        <h2>{{ message2 }}</h2>
        <ul>
          <li v-for="task in taskDone" :key="id" class="liste">
            <Supprimer v-bind:id="task.id" v-bind:todoList="todoList" />

            {{ task.task }}

            <button type="button" name="notDone" @click="task.done = !task.done">Pas Fait</button>

          </li>
        </ul>
      </section>

        
      <!-- <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav> -->
    </div>
  </header>

  <!-- <RouterView /> -->
</template>

<style>
body{
  background-color: rgb(255, 216, 164);
  color: white;
}

.wrapper{
  width:60%;
  margin:1em auto;
  text-align: center;
  font-size: large;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

h2{
  color:rgb(180, 77, 45);
  margin:0;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  font-weight: normal;
}

h1{
  color: rgb(180, 77, 45);
  text-transform: uppercase;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
}

ul{
  list-style: none;
  padding:0;
}

.done{
  background-color: rgb(255, 198, 123);
  border-radius: 10px;
  padding:1em;
  margin:1em auto;  
}

.nDone{
  background-color: rgb(255, 198, 123);
  border-radius: 10px;
  padding:1em;
  margin:1em auto;
}

li {
  margin:1em;
  font-weight: bold;
}
</style>