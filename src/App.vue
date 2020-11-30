<template>
  <div id="app" >
    <div class="container">
      <div class="row">
        <div class="col-12 col-sm-12 col-md-6 col-lg-6 col-xl-6" >
          <div class="imagen" v-for="(item, index) in datosApi" :key="index" >
            <p>{{item.id}}</p>
            <p>{{item.tags[1]}}</p>
            <p>{{item.gif}} hola</p>
              <img src="https://cataas.com/cat"  alt="imagen de gatos">
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
      datosApi: [] ,
      mensaje: {
        saludo: '/says/Hola!!?',
        Despedida: '/says/Chao!!?'
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
      fetch ('https://cataas.com/api/cats')
        .then (resp => resp.json())
        .then (result => {
        this.datosApi = result;
        console.log(this.datosApi)
        })
        
    }
}
</script>

<style>

</style>
