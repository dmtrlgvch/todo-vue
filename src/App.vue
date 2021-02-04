<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
    <h1 class="app__title">{{ title }}</h1>   
    </v-app-bar>

    <v-main>
      <v-container>
        <v-row>
          <v-col cols="4">
            <CreateTodo @create-todo='createTodo'/>
          </v-col>
          <v-col cols="8">
            <TodoList :todos='todos'/>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  import CreateTodo from '@/components/CreateTodo.vue'
  import TodoList from '@/components/TodoList.vue'

  export default {
    name: 'App',
    components: {
      
      CreateTodo,
      TodoList
    },

    data(){
      return {
        
        title: 'Todo Vue App',
        todos: [
          {
            title: 'Todo A',
            text: 'Some description',
          },
          {
            title: 'Todo B',
            text: 'Some description',
          },
          {
            title: 'Todo C',
            text: 'Some description',
          },
      ]
      } 
    },

    methods: {
      createTodo(newTodo) {
        this.todos.push(newTodo)
      }
    }
  };
</script>

