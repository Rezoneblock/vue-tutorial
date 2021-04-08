<template>
  <div id="app">
    <h1 class="title">Todo application</h1>

    <router-view />
  </div>
</template>



<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
.title {
  margin-bottom: 30px;
}
</style>
