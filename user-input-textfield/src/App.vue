<template>
  <div id="app">
    <form @submit.prevent="pressed">
      <UserInputTextField class="mb-5" height="50px" width="200px" name="Username or Email" v-model="input" :error="error" />
      <UserInputTextField class="mb-5" height="50px" width="200px" name="Password" icon="key-fill" type="password" v-model="input" :error="error" />
      <button type="submit">Press ME</button>
    </form>
    
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
      input: "",
      error: false
    }
  },
  methods:{
    pressed(){
      this.error = !this.error
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
.mb-5{
  margin-bottom: 1.5rem;
}
</style>
