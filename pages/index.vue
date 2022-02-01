<template>
  <v-container fluid class="grey lighten-5 contenedor">
    <v-img src="peluches.png" alt="peluches" class="imagenIntro">
    </v-img>
    <h1 class="textoIntro">mandas un dibujo, <br>
      recibís un peluche</h1>

    <v-divider class="dividerProceso"></v-divider>
    <h1 class="procesoTitulo"> Nuestro Proceso </h1>
    <div class="procesoImagen d-flex flex-column align-center">
      <h2>imagen</h2>
      <v-img
        src="imagen.jpeg" 
        alt="imagen"
        class="imagenProceso"
      >
      </v-img>
    </div>
    
    <div class="procesoDiseño d-flex flex-column align-center">
      <h2>diseño</h2>
      <v-img src="diseño.jpeg" alt="" class="imagenProceso">
      </v-img>
    </div>
    
    <div class="procesoProducto d-flex flex-column align-center">
      <h2>producto</h2>
      <v-img src="producto.jpeg" alt="" class="imagenProceso">
      </v-img>
    </div>

    <div class="equipo">
      <h1>Nuestro Equipo</h1>
      <div class="flex-row flex-wrap justify-space-around">

        <div class="flex-column">

          <h2>producto</h2>
          <v-img src="producto.jpeg" class="imagenProceso">
          </v-img>
        </div>
       
        <div class="flex-column">

          <h2>producto</h2>
          <v-img src="producto.jpeg" class="imagenProceso">
          </v-img>
        </div>
      </div>
    </div>

  </v-container>  
</template>

<script>
export default {
  name: 'IndexPagina',
  head() {
    return {
      title: 'Inicio',
      meta: [
        {
          hid: 'Inicio',
          name: 'Inicio',
          content: 'Inicio.'
        }
      ]
    }
  }
}
</script>

<style scoped>
.imagenIntro {
  margin: auto;
  max-height: 70vh;
  grid-area: imagenIntro;
}

.textoIntro {
  margin: 1rem;
  font-size: clamp(1.2rem,1rem + 3.5vw);
  text-align: center;
  grid-area: textoIntro;
  text-transform: uppercase;
}

.dividerProceso {
  margin: 1rem;
  grid-area: dividerProceso;
}

.procesoTitulo {
  margin: 0.4rem;
  grid-area: procesoTitulo;
}

.procesoImagen {
  grid-area: procesoImagen;
}

.procesoDiseño {
  grid-area: procesoDiseño;
}

.procesoProducto {
  grid-area: procesoProducto;
}

.imagenProceso {
  max-width: 90vw;
  max-height: 50vh;
  border-radius: 50%;
}

.equipo {
  grid-area: equipo;
}

.contenedor {
  align-items: center;
  text-align: center;
  display: grid;
  grid-template-areas:
    "imagenIntro"
    "textoIntro"
    "dividerProceso"
    "procesoTitulo"
    "procesoImagen"
    "procesoDiseño"
    "procesoProducto"
    "equipo";
}

@media (min-width: 900px) {

.contenedor {
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-areas:
    "imagenIntro textoIntro textoIntro"
    "dividerProceso dividerProceso dividerProceso"
    "procesoTitulo procesoTitulo procesoTitulo"
    "procesoImagen procesoDiseño procesoProducto"
    "equipo        equipo        equipo       ";
  }

  .imagenProceso {
    max-width: 25vw;
  }

  .textoIntro {
    margin: 2rem;
  }

  .equipo {
    flex-direction: row;
  }

}
</style>
