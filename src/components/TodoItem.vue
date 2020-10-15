<template>
    <div class="todo-item" v-bind:class="{'is-complete': todo.completed}">     <!-- on condition todo.completed is true, implement class is-complete -->
        <p>
            <input type="checkbox" v-on:change="markComplete"/>                 <!-- v-on creates event, using a change event -->
            {{todo.title}}
            <button @click="$emit('del-todo', todo.id)" class="del">x</button>
            </p>
    </div>
</template>

<script>
export default {
    name:"TodoItem",
    props: ["todo"],
    methods: {
        markComplete(){
            this.todo.completed = !this.todo.completed
        }
    }
}
</script>

<style scoped>
    .todo-item {
        background: lightgrey;
        padding: 10px;
        border-bottom: 1px white dotted;
    }

    .is-complete{
        text-decoration: line-through;
    }

    .del{
        background: red;
        color: white;
    }


</style>