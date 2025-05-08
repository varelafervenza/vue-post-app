<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
/* Estilos globales opcionales */
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f4f4f4;
}
#app {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
}
button {
  margin-right: 10px;
}
</style>
