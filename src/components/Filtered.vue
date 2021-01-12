<template>
    <div>
        <h2>Completed Tasks</h2>
         <h3>Total Tasks: {{dat.length}}</h3>
       
           <table class="table" v-if="dat.length !== 0">
            <tr>
               <th>Name</th>
               <th>Date Added</th>
               <th>Deadline</th> 
               <th>Actions</th>
            </tr>
            <tbody>
            
            <tr v-for="todo in dat" v-bind:key="todo.id">
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
</template>

<script>

    export default{
        name:"Filtered",
        props: [
            'todos'
        ],
    
        computed: {
            dat(){
                var compel = this.todos.filter(function (complete){
                    return complete.completed == true;
                });
                return compel;
            }
        }
    }
</script>

<style scoped>

</style>