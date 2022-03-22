<template>
  <nEditor/>
</template>

<script>
import nEditor from './nEditor.vue'

export default {
  name: 'App',
  components: {
    nEditor
  }
}
</script>

<style>
html {
  background-color: #181818;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
  margin-top: 60px;
}
</style>
