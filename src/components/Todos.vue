<template>
    <div>
        <div v-bind:key="todo.id" v-for="todo in todos">
            <TodoItem v-bind:todo="todo" />
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Todos',
    components: {
        TodoItem,
    },
    props: ["todos"]
}
</script>

<style scoped>

</style>
