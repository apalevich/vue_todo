<template>
  <div>
    <Header />
    <AddTodo v-on:add-todo="AddTodo" />
    <Todos v-bind:todos="todosh" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import axios from 'axios';
import Header from '../components/layout/Header.vue';
import Todos from '../components/Todos.vue';
import AddTodo from '../components/AddTodo.vue'

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Home',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todosh: []
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => {
        if (res.status === 200) {
          this.todosh = this.todosh.filter(todo => todo.id !== id)
          console.log('Successfully deleted id:', id);
        } else {
          alert('Please check connection');
        }
      })
      .catch(err => {
        alert('Sorry, something is wrong');
        console.error(err);
      })
    },
    AddTodo(newTodo) {
      console.log('New todo object:', newTodo);
      const { title, completed } = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos',{
        title,
        completed
      })
      .then(res => {
        this.todosh = [...this.todosh, res.data];
        console.log('Successfully added to the list:', this.todosh);
      })
      .catch(err => {
        alert('Sorry, something is wrong');
        console.error(err);
      })
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=4')
    .then(res => {
      if (res.status === 200) {
        this.todosh = res.data;
        console.log('Successfully loaded todos:', this.todosh);
      } else {
        alert('Please check connection');
      }
    })
    .catch(err => {
      alert('Sorry, something is wrong');
      console.error(err);
    })
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
