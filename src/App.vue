<template>
  <div id="app">
    <Main/>
  </div>
</template>

<script>
import Main from './components/Main.vue'

export default {
  name: 'App',
  data(){
    return {
      datosApi: [],
      
    }
  },
  components: {
    Main
  },
  created() {
      fetch ('https://randomuser.me/api')
        .then (resp => resp.json())
        .then (result => {
          this.datosApi = result.results;
          console.log(this.datosApi)
          })
    .catch (error => console.error(error))
    },
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
