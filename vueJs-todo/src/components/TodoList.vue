<template lang="html">
  <div class="">
    <div class="ui dividing centered header">
      <p>Completed Tasks: {{todos.filter(todo=> {return todo.done === true}).length}}</p>
      <p>Pending Tasks: {{todos.filter(todo=> {return todo.done === false}).length}}</p>

    </div>
    <todo v-for="todo in todos" v-bind:todo="todo" :key="todo.id" v-on:delete-todo="deleteTodo"></todo>
  </div>
</template>

<script>

import Todo from './Todo'

export default {
  props: ['todos'],
  components: {
    Todo
  },
  methods: {
    deleteTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos.splice(todoIndex, 1)
    }
  }
}
</script>

<style lang="css">
</style>
