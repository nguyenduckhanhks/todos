<template>
    <div class="footer row">
        <div class="todo-list-count col-xs-3 col-sm-3 col-md-3 col-lg-3">{{todoActiveLeft}} items left</div>
        
        <div class="filter">
            <button v-bind:class="{'filterActive': filter=='All'}" class="col-xs-2 col-sm-2 col-md-2 col-lg-2" @click="changeFilter('All')">All</button>
            <button v-bind:class="{'filterActive': filter=='Active'}" class="col-xs-2 col-sm-2 col-md-2 col-lg-2" @click="changeFilter('Active')">Active</button>
            <button v-bind:class="{'filterActive': filter=='Completed'}" class="col-xs-2 col-sm-2 col-md-2 col-lg-2" @click="changeFilter('Completed')">Completed</button>
        </div>

        <button class="col-xs-3 col-sm-3 col-md-3 col-lg-3" @click="clearCompleted">Clear Completed</button>
    </div>
</template>

<script>
export default {
    props:{
        filter: String,
        clearCompleted: Function,
        todoActiveLeft: Number
    },
    methods:{
        changeFilter(filter){
            this.$emit('changeFilter',filter)
        }
    }
}
</script>

<style>
    .filterActive{
        border: 1px solid black;
    }
</style>