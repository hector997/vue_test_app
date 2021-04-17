<template>
    <div class="todo-item" v-bind:class="{'is-completed': todo.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete">
            {{todo.title}}
            <button @click="$emit('del-todo',todo.id)" class="del">x</button>
        </p>
    </div>
</template>

<script>
export default {
    name: "ToDoItem",
    props: ["todo"],
    data() {
        return {
            todoLocal: this.todo,
        };
    },
    methods: {
        markComplete() {
            console.log("todo completed state changed");
            this.todoLocal.completed = !this.todoLocal.completed;
        }
    }
}
</script>

<style scoped>
    .todo-item{
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }
    .is-completed {
        text-decoration: line-through;
    }
    .del {
        background: #ff0000;
        color: #fff;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
    
</style>