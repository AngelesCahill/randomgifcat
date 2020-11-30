<template>
  <div id="app" >
    <div class="container">
      <div class="row">
        <div class="col">
          <div class="imagen" v-for="(item) in datosApi" :key="item">
              <img :src="datosApi/mensaje&filter&color&tamaño&tipo" alt="imagen de gatos">
          </div>
        </div>
      </div>
    </div>
    
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return {
      datosApi:'',
      mensaje: {
        saludo: 'Hola!!',
        Despedida: 'Chao!!'
      },
     filter: {
       Sepia: 'filter=sepia',
       Blur: 'filter=blur',
       Mono: 'filter=mono',
       Negative: 'filter=negative',
       Paint: 'filter=paint',
       Pixel: 'filter=pixel'
     },
     color: {
       color1: "color=red",
       color2: "color=green",
       color3: "color=black",
       color4: "color=white",
       color5: "color=orange",
       color6: "color=blue"
     },
     tamaño: {
       pequeño: 'size=30',
       mediano: 'size=40',
       grande: 'size=50'
     },
     tipo: {
       small: 'type=sm',
       medium: 'type=md',
       cuadrado: 'type=sq',
       original: 'type=or'
     }
    };
  },
  
  created() {
      fetch ('https://cataas.com/cat/gif/says')
        .then (resp => resp.json())
        .then (result => {
          this.datosApi = result;
        })
        
    }
}
</script>

<style>

</style>
