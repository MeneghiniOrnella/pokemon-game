<template>
  <Page />
</template>

<script>
import Page from './pages/Page.vue';

export default {
  name: 'App',
  components: { Page }
}
</script>

<style>
body{
  background-color: rgb(238, 202, 0);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>
