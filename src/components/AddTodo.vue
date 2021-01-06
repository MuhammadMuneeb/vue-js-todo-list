<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title">
            <button type="submit">Add</button>
        </form>
    </div>
</template>

<script>
import uuid from 'uuid';

export default{
    name: 'AddTodo',
    data(){
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e){
            e.preventDefault();

            const newTodoObj = {
                id: uuid.v4(),
                title: this.title,
                completed: false,
                date: this.dateNow
            }

            this.$emit('add-todo', newTodoObj);
            this.title = '';
        }
    },
    computed: {
        dateNow(){
            var date = new Date();
            return date.getDate()+'/'+date.getUTCMonth()+1+'/'+date.getFullYear();
        }
    }
    
}

</script>