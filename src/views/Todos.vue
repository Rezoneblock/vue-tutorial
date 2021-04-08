<template>
  <div class="container">
    <hr>
    <router-link to="/" class="link-home">Home</router-link>
    <AddTodo @add-todo="addTodo" />
    <select v-model="filter" class="select">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not completed</option>
    </select>
    <hr>
    <Loader v-if="loading"/>
    <TodoList 
      v-else-if="filteredTodos.length"
      v-bind:todos="filteredTodos"
      @remove-todo="removeTodo"
    />
    <p v-else class="no-todos">No todos yet, add some</p>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'
import Loader from '@/components/Loader'
export default {
  name: "app",
  
  data() {
    return {
      todos: [],
      loading: true,
      filter: 'all'
    }
  },
  
  components: {
    TodoList,
    AddTodo,
    Loader
  },

  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
      .then(response => response.json())
      .then(json => {
        this.todos = json
        this.loading = false
      })
  },

  // watch: {
  //   filter(value) {
  //     console.log(value);
  //   }
  // },
  computed: {
    filteredTodos() {
      if (this.filter === 'all') {
        return this.todos;
      }
      if (this.filter === 'completed') {
        return this.todos.filter(t => t.completed)
      }
      if (this.filter === 'not-completed') {
        return this.todos.filter(t => !t.completed)
      }
    }
  },

  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id);
    },
    addTodo(todo) {
      this.todos.push(todo);
    }
  }
}

</script>

<style lang="scss" scoped>
  .link-home {
    color: #000;
  }
  .no-todos {
    margin: 20px 0;
  }
</style>
