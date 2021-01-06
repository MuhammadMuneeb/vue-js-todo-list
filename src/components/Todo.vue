<template>
    <div :class="{'sax':todo.completed , 'incomplete':!todo.completed}">
        
        <p @click="markComplete">{{ todo.title }} - {{todo.date}}</p>
        <button @click="$emit('delete-todo', todo.id)">Delete</button>
    </div>
</template>

<script>
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