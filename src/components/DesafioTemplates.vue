<template>
  <div class="d-flex align-items-center">
    <div class="m-4 p-4 w-50 bg-success">
      <div class="mb-3">
        <label for="colorFondo" class="form-label">Color de Fondo</label>
        <input v-model="colorFondo" type="text" class="form-control" id="colorFondo">
      </div>
      <div class="mb-3">
        <label for="colorTexto" class="form-label">Color de texto</label>
        <input v-model="colorTexto" type="text" class="form-control" id="colorTexto">
      </div>
      <div class="mb-3">
        <label class="me-2" for="mostrarTexto">Mostrar texto</label>
        <input v-model="show" type="checkbox" name="" id="mostrarTexto" />
      </div>
      <div class="mb-3">
        <label for="borde" class="form-label">Borde</label>
        <input v-model="bordeElegido" :min="minimoBorde" :max="maximoBorde" type="range" class="form-range" id="borde">
      </div>
      <div class="mb-3">
        <label for="contenidoTextual" class="form-label">Contenido textual</label>
        <input v-model="mensaje" type="text" class="form-control" id="contenidoTextual">
      </div>
      <div class="mb-3">
        <label for="tipografia" class="form-label">Tipografía</label>

        <select v-model="tipografiaElegida" class="form-select">

          <option id="tipografia" v-for="tipo in tipografias" :key="tipo" :value="tipo" >{{ tipo }}</option>

        </select>

      </div>
      <div class="mb-3">
        <label class="me-2" for="mostrarOpaco">Opaco</label>
        <input v-model="mostrarOpaco" type="checkbox" id="mostrarOpaco" />
      </div>
      <div class="mb-3">
        <label class="me-2">Tamaño de letra</label>
        <div>
          <input id="small" class="form-check-input mt-1" type="radio" value="small" name="size" v-model="tamanioLetra" />
          <label class="me-2 ms-2" for="small">Pequeño</label>

          <input id="medium" class="form-check-input mt-1" type="radio" value="medium" name="size" v-model="tamanioLetra" />
          <label class="me-2 ms-2" for="medium">Mediano</label>

          <input id="large" class="form-check-input mt-1" type="radio" value="large" name="size" v-model="tamanioLetra" />
          <label class="me-2 ms-2" for="large">Grande</label>
        </div>
      </div>
    </div>

    <div class="border border-1 p-4 m-4 w-50 h-50" :style="{backgroundColor: colorFondo, borderRadius: rangoBorde}">
        <p v-show="show" :style="{color: colorTexto, fontStyle: estiloFuente, opacity: esOpaco, fontSize: letraSize}">{{ mensaje }}</p>      
    </div>

  </div>
</template>

<script>
export default {
  name: 'DesafioTemplates',
  data(){
    return{
      colorFondo: this.colorFondo,
      colorTexto: this.colorTexto,
      mensaje: this.mensaje,
      show: true,
      bordeElegido: "",
      minimoBorde: "0",
      maximoBorde: "100",
      tipografias: ["normal", "italic", "oblique"],      
      mostrarOpaco: "",
      opacidad: this.opacidad,
      tamanioLetra: "large",
      tipografiaElegida: this.tipo,
    }
  },
  
  computed: {
    rangoBorde(){
      return this.bordeElegido + "px"
    },
    esOpaco(){
      return this.mostrarOpaco ? 0.5:1
    },
    letraSize(){
      switch (this.tamanioLetra){
        case 'small':
          return '.5rem';
        case 'medium':
          return '1rem';
        case 'large':
          return '2rem';
        default:
          return '0px';
      }
    }, 
    estiloFuente(){
      return this.tipografiaElegida;
    }
  },
}
</script>

<style scoped>

.estilo {
  display: block;
  padding: 1rem;
  margin: 2rem;
  background-color: green;
  width: 50%;
}

.estiloDiv {
  display: inline-block;
}

ul>li{
  list-style: none;
}


</style>
