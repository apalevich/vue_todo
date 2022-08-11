<template>
  <div id="app">
    <Header />
    <AddTodo />
    <Todos v-bind:todos="todosh" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from './components/layout/Header.vue';
import Todos from './components/Todos.vue';
import AddTodo from './components/AddTodo.vue'

export default {
  name: 'App',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todosh: [
        {
           id: 1,
           title: 'Download the docs',
           completed: true,
        },
        {
           id: 2,
           title: 'Finish crash course',
           completed: false,
        },
        {
           id: 3,
           title: 'Explore ecosystem',
           completed: false,
        }
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todosh = this.todosh.filter(todo => todo.id !== id)
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
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
