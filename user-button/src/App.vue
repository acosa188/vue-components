<template>
  <div id="app">
    <user-button height="50px" width="100%" label="SIGN IN" btn_state="success"/>
  </div>
</template>

<script>
import UserButton from './components/UserButton.vue'

export default {
  name: 'App',
  components: {
    UserButton
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
