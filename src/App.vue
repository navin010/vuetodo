<template>
  <div id="app">
    <Header/>
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from './components/Todos';
import Header from './components/layout/Header';
import AddTodo from './components/AddTodo';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo
  },

  data(){
    return{
      todos: []
    }
  },


  methods:{
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id != id)
    },
    addTodo(newTodo){
      this.todos = [...this.todos, newTodo]
    },
    created(){
      axios.get('https://jsonplaceholder.typicode.com/todos')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err))
    }

  }


}
</script>

<style>

body{
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4%;
}


</style>
