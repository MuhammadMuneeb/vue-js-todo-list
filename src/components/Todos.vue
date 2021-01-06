<template>
    <div v-if="todos.length !== 0">
        <h2>My Todolist </h2>
        <h3>Total Tasks: {{todos.length}}</h3>
        <ul>
            <li v-for="todo in todos" v-bind:key="todo.id" >
                <Todo v-bind:todo="todo" v-on:delete-todo="$emit('delete-todo',todo.id)"/>
            </li>
        </ul>
    </div>
    <div v-else>
        <h3>Click on the Add button to create tasks!</h3>
    </div>
</template>

<script>
    import Todo from './Todo';
    

    export default{
        name: 'Todos',
        components: {
            Todo,
        },
        props: [
            "todos"
        ]
    }
</script>
<style scoped>
</style>