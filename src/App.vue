<template>
  <div class="app">
    <Gatos @solicitandoGato="conexionAPI" :url="url"/>
  </div>
</template>

<script>

import Gatos from './Gatos.vue'

export default {
  name: 'App',
  data(){
    return {
      url:'',
    }
  },
  components: {
    Gatos
  },
  methods: {
    async conexionAPI(data){
      console.log(data);
      try {
        let resp = await fetch(`https://cataas.com/cat/gif/says/${data.titulo}?filter=${data.filtro}&color=${data.color}&size=${data.tamano}`);
        this.url = resp.url
      } catch (error) {
        console.error(error);
      }
    }
  },
} 

</script>

<style>

</style>
