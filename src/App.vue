<template>
  <div id="app">
    <Header />
    <ToDoContainer />
  </div>
</template>

<script>

import Header from './components/Header/Header'
import ToDoContainer from './components/ToDoContainer/ToDoContainer'

export default {
  name: 'App',
  components: {
    Header,
    ToDoContainer
  }
}
</script>

<style>
body {
    margin: 0;
}
button {
    cursor: pointer
}
#app {
    min-height: 100vh;
}
.strike {
    text-decoration: line-through;
}
</style>
