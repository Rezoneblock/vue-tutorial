<template>
  <form @submit.prevent="onSubmit" class="form">
    <input type="text" v-model="title">
    <button type="submit" class="button-create">Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: ''
    }
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          complited: false
        }
        
        this.$emit('add-todo', newTodo);
        this.title = '';
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  .form {
    margin: 10px 0;
    display: flex;
    justify-content: center;
  }
  .button-create {
    margin-left: 10px;
    padding: 3px;
    background-color: #fff;
    border: 1px solid;
    border-radius: 10%;
    transition: .4s;
    cursor: pointer;
    &:hover {
      transform: scale(1.2)
    }
  }
</style>