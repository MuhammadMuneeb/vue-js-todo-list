<template>
    <div>
        <h2>My Todolist</h2>
        <ul>
            <li v-for="todo in todos" v-bind:key="todo.id">
                <Todo v-bind:todo="todo" v-on:delete-todo="$emit('delete-todo', todo.id)"/>
            </li>
        </ul>
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