<template>
  <ul>
    <input v-model="newTodo" placeholder="new todo" @keyup.enter="addTodo">
    <li v-for="(todo, index) in todos">
      <item :todo="todo"></item>
      <button @click="removeTodo(index)">X</button>
    </li>
  </ul>
</template>

<style>
  body, input, button {
    font-family: Arial;
    font-size: 30px;
    margin: 10px;
  }
  button {
    color: #000;
  }
</style>

<script>
  import Item from './Item.vue';

  export default {
    components: { Item },
    data () {
      return {
        newTodo: '',
        todos: [
          { text: 'One item', added: new Date() }
        ]
      }
    },
    methods: {
      addTodo: function () {
        const text = this.newTodo.trim();
        if (text) {
          this.todos.push({
            text: text,
            added: new Date()
          });
          this.newTodo = '';
        }
      },
      removeTodo: function (index) {
        this.todos.splice(index, 1)
      }
    }
  }
</script>