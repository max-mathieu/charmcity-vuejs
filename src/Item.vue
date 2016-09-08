<template>
  <span>
    <span v-if="editMode"><input v-model="todo.text" @keyup.enter="editMode=false"></span>
    <span v-else>{{ todo.text }} <button @click="editMode=true">Edit</button></span>
    <br>
    <small>{{ added }}</small>
  </span>
</template>

<style scoped>
  button {
    color: #f00;
  }
</style>

<script>
  export default {
    props: [ 'todo' ],
    data () {
      return {
        editMode: false
      }
    },
    computed: {
      added() {
        return this.todo.added.toLocaleString()
      }
    }
  }
</script>