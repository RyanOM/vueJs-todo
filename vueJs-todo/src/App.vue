<template>
  <div>
    <h1 class="ui dividing centered header">VueJS Todo App</h1>
    <todo-list v-bind:todos="todos"></todo-list>
    <create-todo v-on:create-todo="createTodo"></create-todo>
  </div>
</template>

<script>
import TodoList from './components/TodoList'
import CreateTodo from './components/CreateTodo'
import swal from 'sweetalert'

export default {
  name: 'App',
  components: {
    TodoList,
    CreateTodo
  },

  methods: {
    createTodo (newTodo) {
      this.todos.push(newTodo)
      swal('Success!', 'To-Do created!', 'success')
    }
  },

  // data to template
  data () {
    return {
      todos: [{
        title: 'Learn Vue.js',
        project: 'Learning',
        done: false
      }, {
        title: 'Deploy Vue.js Todo app',
        project: 'Perso Projects',
        done: true
      }, {
        title: 'Add another todo item to the list',
        project: 'Perso Projects',
        done: false
      }]
    }
  },
  watch: {
    todos: {
      handler () {
        localStorage.setItem('todos', JSON.stringify(this.todos))
      },
      deep: true
    }
  },
  mounted () {
    if (localStorage.getItem('todos')) this.todos = JSON.parse(localStorage.getItem('todos'))
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
