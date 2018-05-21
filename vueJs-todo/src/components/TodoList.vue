<template lang="html">
  <div class="">
    <p>Completed Tasks: {{todos.filter(todo=> {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo=> {return todo.done === false}).length}}</p>
    <todo v-for="todo in todos" v-bind:todo="todo"></todo>
  </div>
</template>

<script>

import Todo from './Todo';

export default {
  props: ['todos'],
  components: {
    Todo,
  }
}
</script>

<style lang="css">
</style>
