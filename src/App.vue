<template>
  <div id="app">
  <Todos v-bind:todos="todos" v-on:delete-todo="deleteTodo" />
  <AddTodo v-on:add-todo="addTodo"/>
  </div>
</template>

<script>

import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
export default {
  components: { Todos, AddTodo },
  name: 'App',
  data(){
    return {
      todos: [
         
      ]
    }
  },
  methods:{
    addTodo(newTodoObj){
      this.todos = [...this.todos, newTodoObj];
    },
    deleteTodo(todoId){
      this.todos = this.todos.filter(todo => todo.id !== todoId)
    }
  }
}
</script>

<style>

</style>
