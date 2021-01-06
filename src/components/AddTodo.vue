<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title">
            <input type="date" v-model="deadline" name="deadline">
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
            title: '',
            deadline: ''
        }
    },
    methods: {
        addTodo(e){
            e.preventDefault();

            const newTodoObj = {
                id: uuid.v4(),
                title: this.title,
                completed: false,
                date: this.dateNow,
                deadline: this.deadline
            }

            this.$emit('add-todo', newTodoObj);
            this.title = '';
            this.deadline ='';
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