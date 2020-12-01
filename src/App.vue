<template>
  <div id="app" >
    
    <div class="container">
    <h1 class="text-center my-5">Busca tu Gato</h1>
    <div class="p-5 bg-light">
      <form @submit.prevent="solicitarGato">
        <div class="form-group">
          <label for="titulo">Titulo: </label>
          <input type="text" class="form-control" v-model="titulo">
        </div>

        <div class="form-group">
          <label for="filtro">Filtro: </label>
          <select class="form-control" v-model="filtro">
            <option value="blur">Blur</option>
            <option value="mono">Mono</option>
            <option value="sepia">Sepia</option>
            <option value="negative">Negative</option>
            <option value="paint">Paint</option>
            <option value="pixel">Pixel</option>
          </select>
        </div>

        <div class="form-group bloque">
          <label for="color">Color: </label>
          <select class="form-control colores" v-model="color">
            <option value="red">Rojo</option>
            <option value="green">Verde</option>
            <option value="white">Blanco</option>
            <option value="yellow">Amarillo</option>
            <option value="blue">Azul</option>
          </select>
        </div>
        <span class="circulo" :style="{backgroundColor : color}"></span>

        <div class="form-group">
          <label for="tamano">Tamaño: </label>
          <input type="number" class="form-control" v-model="tamano">
        </div>
        
        <button type="submit" class="btn btn-primary">Buscar</button>
      </form>
    </div>
    <hr>
    <div class="p-5 bg-light border border-dark w-100" v-if="url">
      <h3 class="text-center"><em>Tu gato:</em></h3>
      <img :src="url" alt="gato" class="img-fluid">
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
        saludo: 'says/Hola!!?',
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
      fetch ('https://cataas.com/api/cat')
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
