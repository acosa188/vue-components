<template>
  <div id="app">
    <UserInputTextField height="50px" width="200px" name="Username or Email" v-model="input"/>
  </div>
</template>

<script>
import UserInputTextField from './components/UserInputTextField.vue'

export default {
  name: 'App',
  components: {
    UserInputTextField
  },
  data(){
    return{
      input: ""
    }
  }
}
</script>

<style>
html,body{
  height: 100%;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}
</style>
