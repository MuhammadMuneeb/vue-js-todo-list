<template>
    <div>
        <form @submit="addTodo">
         <p v-if="errors.length">
             <b>Please correct the following:</b>
             <ul>
                 <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
             </ul>
         </p>
            <div class="form-group">
            <label id="title">Task Name</label>
            <input type="text" v-model="title" name="title" class="form-control">
            </div>
            <div class="form-group">
            <label id="deadline">Task Deadline</label>
            <input type="date" v-model="deadline" name="deadline" class="form-control">
            </div>
            <b-button type="submit" variant="success">Add</b-button>
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
            deadline: '',
            errors: []
        }
    },
    methods: {
        addTodo(e){
            e.preventDefault();

            if(this.title && this.deadline){
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
            this.errors = [];
                        }

            if(!this.title){
                this.errors.push('Title Required!');
            }

            if(!this.deadline){
                this.errors.push('Deadline required!');
            }
            
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