<template lang="html">
  <div class="">
    <div class="ui dividing centered header">
      <p>Completed Tasks: {{todos.filter(todo=> {return todo.done === true}).length}}</p>
      <p>Pending Tasks: {{todos.filter(todo=> {return todo.done === false}).length}}</p>

    </div>
    <todo v-for="todo in todos" v-bind:todo="todo" :key="todo.id" v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo"></todo>
  </div>
</template>

<script>

import Todo from './Todo'
import swal from 'sweetalert'

export default {
  props: ['todos'],
  components: {
    Todo
  },
  methods: {
    deleteTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos.splice(todoIndex, 1)
    },
    completeTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      if (!this.todos[todoIndex].done) {
        this.todos[todoIndex].done = true
        swal('Success!', 'Todo completed!', 'success')
      } else {
        this.todos[todoIndex].done = false
      }
    }
  }
}
</script>

<style lang="css">
</style>
