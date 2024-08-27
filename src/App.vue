<template>
  <div id="app" class="container my-5">
    <div class="row justify-content-center">

      <div class="col-md-4 bg-dark text-light p-4 rounded">
        <h5 class="mb-3">Color de Fondo</h5>
        <input v-model="colorFondo" class="form-control mb-3" placeholder="Ingresa un color para el fondo">

        <div>
          <h5 class="mb-3">Color del Texto</h5>
          <input v-model="colorTexto" class="form-control mb-3" placeholder="Ingresa un color para el texto">
        </div>
        <div>
          <h5 class="mb-3">Mostrar el Texto
            <input type="checkbox" v-model="mostrarTexto">
          </h5>
        </div>
        <div>
          <h5 class="mb-3">Borde</h5>
          <input type="range" v-model="borde" min="0" max="50" step="1">
        </div>
        <div>
          <h5 class="mb-3 mt-4">Contenido Textual</h5>
          <textarea v-model="contenidoTexto" class="form-control"
            placeholder="Escribe lo que quieras aquí..." maxlength="15"></textarea>
        </div>
        <div>
          <h5 class="mb-3 mt-4">Tipografía</h5>
          <select v-model="tipografiaTexto" class="form-select mb-3">
            <option disabled value="">Selecciona una tipografía</option>
            <option v-for="letra in tipografias" :key="letra" :value="letra">{{ letra }}</option>
          </select>
        </div>
        <div>
          <h5 class="mb-3">Opacidad
            <input type="checkbox" v-model="opacidad">
          </h5>
        </div>
        <div>
          <h5 class="mb-3">Tamaño de Letra</h5>
          <div class="form-check">
            <input type="radio" id="pequeno" value="pequeno" v-model="tamanoLetra" class="form-check-input">
            <label for="pequeno" class="form-check-label">Pequeño</label>
          </div>
          <div class="form-check">
            <input type="radio" id="mediano" value="mediano" v-model="tamanoLetra" class="form-check-input">
            <label for="mediano" class="form-check-label">Mediano</label>
          </div>
          <div class="form-check">
            <input type="radio" id="grande" value="grande" v-model="tamanoLetra" class="form-check-input">
            <label for="grande" class="form-check-label">Grande</label>
          </div>
        </div>
      </div>

      <div class="col-md-6 text-dark p-4 rounded ms-4">
        <div class="text-center">
          <div v-show="mostrarTexto" 
            :style="{
              backgroundColor: colorFondo,
              color: colorTexto,
              borderRadius: borde + 'px',
              fontFamily: tipografiaTexto,
              opacity: opacidad ? 0.5 : 1,
              width: anchoDiv,
              height: altoDiv,
              lineHeight: alturaTexto,
            }" 
            :class="tamanoLetra" 

            class="mx-auto text-center">
            {{ contenidoTexto }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      colorFondo: "",
      colorTexto: "",
      mostrarTexto: true,
      borde: 25,
      contenidoTexto: "",
      tipografiaTexto: "roboto",
      tipografias: ["sans-serif", "open sans", "cursive", "monospace", "fantasy"],
      opacidad: false,
      tamanoLetra: "",
      anchoDiv:"300px",
      altoDiv:"300px",
      alturaTexto: "300px",
    };
  }
};
</script>

<style scoped>
.pequeno {
  font-size: 10px;
}

.mediano {
  font-size: 20px;
}

.grande {
  font-size: 30px;
}

#app {
  max-width: 1200px;
  margin: auto;
}
</style>
