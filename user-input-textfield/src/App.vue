<template>
  <div id="app">
    <input-vue v-model="userName" label="username" class="mb-5" :error="error" width="300px" height="60px"/>
    <input-vue v-model="password" label="password" type="time" width="300px"/>
    <button @click="clickMe">Click ME</button>
  </div>
</template>

<script>
import InputVue from './components/UserInputTextField.vue'

export default {
  name: 'App',
  components: {
    InputVue
  },
  data(){
    return{
      userName: "",
      password: "",
      error: false
    }
  },
  methods:{
    clickMe(){
      this.error = !this.error;
    }
  }
}
</script>

<style>
html,body{
  height: 100%;
  overflow: hidden;
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.mb-5{
  margin-bottom: 1.5rem;
}
</style>
