<template>
    <form class="form-todo-input label-row" @submit="submitAddTodoItem($event,todo)">
        <input v-model="todo" type="text" id="todo-input"/>
    </form>
</template>

<script>
export default {
    data(){
        return{
            todo:''
        }
    },
    props:{
        addTodoItem: Function
    },
    methods:{
        submitAddTodoItem($event, todo){
            this.addTodoItem($event,todo);
            this.todo=''
        }
    }
}
</script>

<style>

</style>