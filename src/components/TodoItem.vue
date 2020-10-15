<template>
    <div>
        <p>{{todo.title}}</p>
    </div>
</template>

<script>
export default {
    name:"TodoItem",
    props: ["todo"]
}
</script>

<style scoped>
    .todo-item {
        background: white;
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