<script>
let id = 0


export default {
  data() {
    return {
      newTodo: '',
      hideCompleted: false,
      todos: [
        { id: id++, text: 'Learn HTML', done: true },
        { id: id++, text: 'Learn JavaScript', done: true },
        { id: id++, text: 'Learn Vue', done: false }
      ]
    }
  },
  computed: {
    filteredTodos() {
      return this.todos.filter(todo => {
        return !todo.done || !this.hideCompleted
      })
    }
  },
  methods: {
    addTodo() {
      this.todos.push({ id: id++, text: this.newTodo, done: false })
      this.newTodo = ''
    },
    removeTodo(todo) {
      this.todos = this.todos.filter((t) => t !== todo)
    }
  }
}
</script>

<template>

  <h3> MY TO DO LIST </h3>

  <form @submit.prevent="addTodo">
    <input v-model="newTodo">


    <button class:add-button>Add Activity</button>

  </form>

  <ul style="list-style-type: none;">
    <li v-for="todo in filteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done">
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>


  <br>

  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? 'Show all' : 'Hide completed' }}
  </button>

</template>

<style>
.done {
  text-decoration: line-through;
}


</style>
