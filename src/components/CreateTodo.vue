<template>
  <v-form v-model="valid">
    <p> {{todoTitle}} {{todoText}}</p>
    <v-text-field
      v-model="todoTitle"
      label="What do you want to do?"
      required
    ></v-text-field>
    <v-textarea
      v-model="todoText"
      outlined
      label="Describe this"
      required
    ></v-textarea>
    <v-btn
      @click="createTodo"
      class="btn-submit"
      color="primary"
      elevation="2"
      x-large
    >
      Submit
    </v-btn>
    <v-btn
      @click="clearTodo"
      color="error"
      elevation="2"
      x-large
    >
      Clear
    </v-btn>
  </v-form>      
</template>

<script>

  export default {
    name: 'CreateTodo',
    data() {
      return {
        valid: true,
        todoTitle: '',
        todoText: '',
      }
    },

    methods: {
      createTodo() {
        if (this.todoTitle.length > 0 && this.todoText.length > 0) {
          let title = this.todoTitle;
          let text = this.todoText;

          this.$emit('create-todo', {
            title,
            text,
          });

          this.todoTitle = '';
          this.todoText = '';
        }
      },

      clearTodo() {
        this.TodoTitle = ''
        this.todoText = ''
      }
    }

  }
</script>

<style >
.btn-submit {
  margin-right: 30px;
}
</style>