<template>
    <!-- <div :class="{'sax':todo.completed , 'incomplete':!todo.completed}"> -->
        <div>
        <!-- <p @click="markComplete">{{ todo.title }} - {{todo.date}} - Deadline: {{todo.deadline}} </p> -->
        <table class="table">
            <tr>
               <th>Name</th>
               <th>Date Added</th>
               <th>Deadline</th> 
               <th>Actions</th>
            </tr>
            <tbody>
            <tr v-for="todo in todos" v-bind:key="todo.id">
                <td>{{ todo.title }}</td>
                <td>{{ todo.date }}</td>
                <td>{{ todo.deadline }}</td>
                <td><button @click="$emit('delete-todo', todo.id)">Delete</button></td>

                <!-- <Todo v-bind:todo="todo" v-on:delete-todo="$emit('delete-todo',todo.id)"/> -->
            </tr>
            </tbody>
            </table>
        
    </div>
        
        
        
</template>

<script>

// import Todos from './Todos';

export default {
    name: 'Todo',
    props: ['todo'],
    methods: {
        markComplete(){
            this.todo.completed = !this.todo.completed
        }
    }
}
</script>

<style scoped>

.incomplete {
    font-size: 30px;
}

.sax {
    text-decoration: line-through;
    font-size: 25px;
    color: red;
  }
</style>