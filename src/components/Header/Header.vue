<template>
  <header class="container-fluid">
    <span><strong>{{title}}</strong></span>
  </header>
</template>

<script>
export default {
    data() {
      return {
        title: 'To Do App with Vue.js'
    }
    }
}
</script>

<style scoped>
  header {
    display: grid !important;
    align-content: center;
    font-size: 3em;
    color: #50514F;
    padding: auto 0 !important;
    height: 100px;
    background-color: #FFE066;
    text-align: center;
    margin-bottom: 50px;
}
</style>