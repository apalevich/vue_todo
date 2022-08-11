<template>
    <div
        class="todo-item"
        v-bind:class="{'is-complete': todo.completed}"
    >
        <input type="checkbox" v-on:click="markComplete">
        <p class="description">{{todo.title}}</p>
        <button class="del" @click="$emit('del-todo', todo.id)">x</button>
    </div>
</template>

<script>
export default {
    name: 'TodoItem',
    props: ['todo'],
    methods: {
        markComplete() {
            // eslint-disable-next-line vue/no-mutating-props
            this.todo.completed = !this.todo.completed
        }
    }
}
</script>

<style scoped>
    .todo-item {
        display: flex;
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .is-complete {
        text-decoration: line-through;
    }

    input[type="checkbox"] {
        margin: 0px 8px;
    }

    .description {
        flex-grow: 1;
        line-height: 1.7;
    }

    .del {
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 5px 10px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>