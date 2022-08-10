<template>
  <div id="app">
    <Todos v-bind:todos="todosh" />
  </div>
</template>

<script>
import Todos from './components/Todos.vue';

export default {
  name: 'App',
  components: {
    Todos
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
</style>
