<template>
 <div id = "App">
   <Header />
   <AddTodo v-on:add-todo="addTodo" />
   <ToDos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
 </div>
</template>

<script>
import ToDos from './components/ToDos';
import Header from './components/layout/header.vue';
import AddTodo from './components/addTodo';

export default {
  name: 'App',
  components: {
      ToDos,
      Header,
      AddTodo
  },
  data() {
    return {
        todos: [
          {
            id:1,
            title: "ToDo One",
            completed: false
          },
          {
            id:2,
            title: "ToDo Two",
            completed: true
          },
          {
            id:3,
            title: "ToDo three",
            completed: false
          },
        ]
      }
    },
    methods: {
        deleteTodo(id) {
          this.todos = this.todos.filter(todo => todo.id !== id);
        },
        addTodo(newTodo){
          console.log(this.title);
          this.todos = [...this.todos, newTodo];
        }
      }
}
</script>

<style>
  *{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
   }

   body{
     font-family: Arial, Helvetica, sans-serif;
     line-height: 1.4;
  }
  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover {
    background: #666;
  }
  
</style>
