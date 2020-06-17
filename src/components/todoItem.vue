<template>
    <div class="todo-list">
        <div class="label-row">
            <i class="fa fa-check-circle checked" @click="toggleComplete(index)"></i>
                <span v-bind:class="{'todoChecked': item.complete}" >{{item.todo}}</span>
            <i v-bind:class="{'fa fa-times remove': item.complete}" @click="removeTodo(item)"></i>
        </div>
    </div>
</template>

<script>
export default {
    props:{
        item: Object,
        index: Number,
        removeTodo: Function,
        toggleTodoItemComplete: Function
    },
    methods:{
        toggleComplete(index){
            this.item.complete = !this.item.complete;
            this.toggleTodoItemComplete(index);
        }
    }
}
</script>

<style>
    .todoChecked{
        text-decoration: line-through;
    }
</style>