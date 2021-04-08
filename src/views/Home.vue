<template>
  <div class="container">
    <h2>Home page</h2>
    <p class="description">Lorem ipsum dolor sit amet consectetur adipisicing elit. Soluta, id quia provident impedit repellendus ex placeat aut, illo eum accusamus dolorum atque, saepe necessitatibus fugiat suscipit. Iusto totam est harum.</p>

    <router-link to="/todos" class="link-todos">Todos</router-link>
  </div>
</template>

<style lang="scss" scoped>
  .container {
    max-width: 550px;
    margin: 0 auto;
  }
  .description {
    margin: 10px 0;
  }
  .link-todos {
    color: #000;
  }
</style>
  