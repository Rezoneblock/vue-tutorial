<template>
  <li class="item">
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" class="input" @change="todo.completed = !todo.completed">
      <strong>{{index + 1}}</strong>
      {{todo.title | uppercase}}
    </span>
    <button class="button" @click="$emit('remove-todo', todo.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase();
    }
  }
}
</script>

<style lang="scss" scoped>
  .item {
    width: 100%;
    padding: 10px;
    margin: 5px 0;
    display: flex; 
    justify-content: space-between;
    align-items: center;
    border: 1px solid;
    transition: .4s; 
    &:hover {
      background-color: gray;
    }
  }
  .button {
    height: 30px;
    width: 30px;
    border: none;
    border-radius: 50%;
    background-color: rgb(245, 52, 52);
    cursor: pointer;
    transition: .4s;
    &:hover {
      transform: scale(1.1)
    }
  }
  .input {
    margin-right: 10px;
    cursor: pointer;
    transition: .4s;
    &:hover {
      transform: scale(1.5)
    }
  }
  .done {
    text-decoration: line-through;
  }
</style>