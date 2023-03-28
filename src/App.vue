<template>
  <div id="app">
    <CreateProcess/>
  </div>
</template>

<script>
import CreateProcess from "./components/CreateProcess.vue";
export default {
  name: 'App',
  components: {
    CreateProcess
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
