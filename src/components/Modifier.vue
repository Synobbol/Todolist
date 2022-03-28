<script>
    export default{
        props: {
            id: Number,
            todoList: Array
        },

        
        data(){
            return{ 
                insideTask:""
            }
        },

        methods:{
            changeTask(){
            let oldIndex = this.id;
            let oldTask = this.todoList.at(oldIndex);

            const rewrite = {
                id: oldIndex,
                task: this.insideTask,
                done: this.done = false,
            }

            Object.assign(oldTask, rewrite);
            this.insideTask = "";

            }
        }
    }
</script>

<template>
    <div class="zoneMod">
        <button  id="mod" type="button" name="notDone" @click="changeTask()">Modifier</button>
        <input class="hide" type="text" id="task" v-model="insideTask">
    </div>
</template>

<style>
#mod{
    margin-right: .5em;
    background-color: rgb(46, 52, 82);
}
#mod:hover{
    background-color: rgb(80, 104, 180);
    transition: background-color 1s;
}

.zoneMod{
    display: flex;
    justify-content: center;
    width:100%;
    margin: 0.5em;
}
.hide{
    width:20%;
    display:none;
}
.zoneMod:hover .hide{
    display:block;
}
</style>