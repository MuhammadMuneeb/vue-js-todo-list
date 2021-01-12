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
            <tr v-for="todo in todos" v-bind:key="todo.id" :class="{'completed':todo.completed}">
                <td>{{ todo.title }}</td>
                <td>{{ todo.date }}</td>
                <td>{{ todo.deadline }}</td>
                <td>
                    <button class="btn btn-primary" @click="completeTask(todo.id)">Mark Completed!</button>
                    <button class="btn btn-danger" @click="$emit('delete-todo', todo.id)">Delete</button></td>
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
        ],
        methods:{
            completeTask(todo_id){
                console.log(todo_id);
                console.log(this.todos[0].id);
                // for(var i =0;i<this.todos.length;i++){
                //     if(this.todos[i].id == todo_id){
                //         this.todos[i].completed = true;
                //         break;
                //     }
                // }
                var compel = this.todos.filter(function(com){
                    return com.completed = true
                })
                return compel
            }
        }
    }
</script>
<style scoped>
.completed{
    color:green;
}
</style>