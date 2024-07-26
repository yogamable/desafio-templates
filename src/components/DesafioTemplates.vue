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
        <select class="form-select">
          <option v-for="tipo in tipografias" :key="tipo" id="tipografia">{{ tipo }}</option>
        </select>
      </div>
      <div class="mb-3">
        <label class="me-2" for="mostrarOpaco">Opaco</label>
        <input v-if="mostrarOpaco" v-model="textoConOpacidad" type="checkbox" name="" id="mostrarOpaco" @change="funcionOpacidad" />
      </div>
      <div class="mb-3">
        <label class="me-2">Tamaño de letra</label>
        <div>
          <input class="form-check-input mt-1" type="radio" value="small" id="small" name="size" v-model="small" @change="funcionSize" />
          <label class="me-2 ms-2" for="small">Pequeño</label>

          <input class="form-check-input mt-1" type="radio" value="mediano" id="mediano" name="size" v-model="medium" @change="funcionSize" />
          <label class="me-2 ms-2" for="medium">Mediano</label>

          <input class="form-check-input mt-1" type="radio" value="grande" id="grande" name="size" v-model="large" @change="funcionSize" />
          <label class="me-2 ms-2" for="large">Grande</label>
        </div>
      </div>
    </div>

    <div class="border border-1 p-4 m-4 w-50 h-50" :style="{backgroundColor: colorFondo, borderRadius: rangoBorde}">
        <p v-show="show" :style="{color: colorTexto, 'font-style': tipografias, opacity: opacidad, fontSize: size}">{{ mensaje }}</p>      
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
      mostrarOpaco: true,
      opacidad: this.opacidad,
      size: this.size,
      small: true,
      medium: true,
      large: true,
    }
  },
  methods: {
    funcionOpacidad(){
      if(this.mostrarOpaco===true){
        this.opacidad = '0.5'
      }else if (this.mostrarOpaco===false){
        this.opacidad = '1'
      }
    },
    
    funcionSize(){
      if(this.small===true){
        this.size = '.5rem'
      }if(this.medium===true){
        this.size = '1.5rem'
      }
    }
  },

  computed: {
    rangoBorde(){
      return this.bordeElegido + "px"
    }
  }
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
