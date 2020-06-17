<template>
  <div id="app">
    <div class="main-container">
      <AddForm
        :addTodoItem="addTodoItem"
      />
      <div v-for="(item,index) in this.filterTodos()" :key="index">
        <TodoItem
          :item="item"
          :index="index"
          :toggleTodoItemComplete="toggleTodoItemComplete"
          :removeTodo="removeTodo"
        />
      </div>
      
      <Filters :todoActiveLeft="todoLeft" :filter="filter" @changeFilter="filter=$event" :clearCompleted="clearCompleted"/>
    </div>
  </div>
</template>

<script>

import AddForm from './components/addForm';
import TodoItem from './components/todoItem';
import Filters from './components/filters';
import './assets/style.css';

export default {
  name: 'App',
  components: {
    AddForm,
    TodoItem,
    Filters
  },
  data(){
    return{
      todos:[],
      todoLeft:0,
      filter: 'All'
    }
  },
  methods:{
    addTodoItem(event, todo){
      event.preventDefault();
      this.todoLeft++;
      this.todos.push({
        todo,
        complete: false
      });
    },

    toggleTodoItemComplete(index){
      var complete = this.todos[index].complete;
      this.todos[index].complete = !complete;
      if(complete===true) this.todoLeft++; else this.todoLeft--;
    },

    removeTodo(todo){
      this.todos.splice(this.todos.indexOf(todo),1);
    },

    filterTodos(){
      if(this.filter == 'All') return this.todos
      if(this.filter == 'Active'){
        return this.todos.filter(todo=>todo.complete == false)
      }
      if(this.filter == 'Completed'){
        return this.todos.filter(todo=>todo.complete == true)
      }
    },

    clearCompleted(){
      this.todos =  this.todos.filter(todo=>todo.complete == false)
    }
  }
}
</script>

<style>

</style>
