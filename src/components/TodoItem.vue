<template>
    <div class="todo-item" 
         v-bind:class="{'is-complete':todo.completed}">
         <p>
            <ul>
              <li><input type="checkbox" v-on:change="markComplete"></li>
              <li><b>Title</b>:{{todo.title}}</li>
              <li><b>Text</b>:{{todo.text}}</li>
            </ul>
            <button @click="$emit('del-todo',todo.id)"  class="del">X</button>
        </p>
    </div>
</template>

<script>

export default {
    name:"TodoItem",
    props:["todo"],
    methods: {
        markComplete() {
            this.todo.completed=!this.todo.completed;
        }
    },
}
</script>

<style scoped>
  .todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }
  .is-complete {
    text-decoration: line-through;
  }
  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>