<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo Title">
            <input type="text" v-model="text" name="text" placeholder="Add Todo Task">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
//import { v4 as uuid } from 'uuid';
export default {
    name: "AddTodo",
    data() {
        return {
            title: '',
            text:''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo={
                title:this.title,
                text:this.text,
                completed:false
            }
            this.$emit('add-todo',newTodo);
            this.title='';
            this.text='';
        }
    },
}
</script>

<style scoped>
  form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
</style>