<template>
    <div v-if="todos.length !== 0">
        <h2>My Todolist </h2>
        <h3>Total Tasks: {{todos.length}}</h3>
       
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
            </tr>
            <tr>
            </tr>
            </tbody>
            </table>
    </div>
        <div v-else>
        <h3>Click on the Add button to create tasks!</h3>
        </div>
</template>

<script>
    

    export default{
        name: 'Todos',
        data(){
        },
        props: [
            "todos"
        ]
    }
</script>
<style scoped>
</style>