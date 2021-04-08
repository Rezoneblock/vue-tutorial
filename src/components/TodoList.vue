<template>
  <div>
    <ul class="list">
      <TodoItem 
        v-for="(todo, i) of todos"
        v-bind:todo="todo"
        v-bind:index="i"
        :key="todo.id" 
        @remove-todo="removeTodo"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'
export default {
  props: ['todos'],
  components: {
    TodoItem,
  },
  methods: {
    removeTodo (id) {
      this.$emit('remove-todo', id);
    }
  }
}
</script>

<style lang="scss" scoped>
  .list {
    margin-left: auto;
    margin-right: auto;
    margin-top: 50px;
    max-width: 550px;
    list-style: none;
    display: flex;
    flex-direction: column;
  }
</style>