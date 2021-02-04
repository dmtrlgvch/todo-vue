<template>
  <v-list >
    <TodoItem @delete-todo='deleteTodo' v-for="(todo) in todos" :todo="todo" :key="todo.title"/>
  </v-list>
</template>

<script>
import TodoItem from '@/components/TodoItem.vue'

export default {
  name: 'TodoList',
  props: {
    todos: Array
  },
  components: {
    TodoItem
  },
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo)
      return this.todos.splice(todoIndex, 1)
    }  
  }
}
</script>
