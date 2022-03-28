<script>
    export default{
        props:{
            id: Number,
            todoList: Array
        },
        
        methods:{
            delTask(){
                let index = this.id;
                this.todoList.splice(index, 1);
            },
        }
    }
</script>

<template>
    <button id="suppr" type="button" name="delete" @click="delTask()">Suppr.</button>
</template>

<style>

#suppr{
    background-color: rgb(161, 25, 25);
}
#suppr:hover{
    background-color: red;
    transition: background-color .5s;
}
</style>