<template>
  <div>
    <v-list-item>
        <v-list-item-content>
          <v-list-item-title>{{ todo.title }}</v-list-item-title>

          <v-list-item-subtitle :class="{ completed: completed }">{{ todo.text }}</v-list-item-subtitle>
        </v-list-item-content>

        <v-list-item-action>
          <v-btn
            @click="completeTodo"
            class="btn-complete"
            small
            color="primary"
            dark
          >
            Complete
          </v-btn>
          <v-btn 
            @click="deleteTodo(todo)"
            small 
            color="error"
          >
            Delete
          </v-btn>
        </v-list-item-action>
        
    </v-list-item>
    <v-divider></v-divider>
  </div>  
</template>

<script>
export default {
  name: 'TodoItem',
  props: {
    todo: Object
  },
  data() {
    return{
      completed: false
    }
  },
  methods: {
      completeTodo() {
        this.completed = !this.completed
      },
      deleteTodo(todo) {
        console.log(todo);
        this.$emit('delete-todo', todo);
      },
  }
}
</script>
<style>
  .completed{
    text-decoration: line-through;
  }
</style>
