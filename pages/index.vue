<template>
  <v-container fluid class="grey lighten-5 contenedor">
    <div class="intro d-flex align-center">

      <v-img src="peluches.png" alt="peluches" class="imagenIntro">
      </v-img>
      <div class="textoIntro">
        <h1 class="text-h4 mb-3">
          Mandas una foto, 
          <br>
          recibís un peluche.
        </h1>
        <NuxtLink to="productos">
          <v-btn
            dark
            color='#52a73c'
            elevation=0
            x-large
            class="botonPedido"
          > 
            buenas, quiero uno
          </v-btn>
        </NuxtLink>
      </div>
    </div>

    <v-divider class="dividerProceso"></v-divider>

    <h1 class="procesoTitulo text-h3"> Nuestro Proceso </h1>
    <div class="procesoImagen d-flex flex-column align-center">
      <h2 class="text-h4">Imagen</h2>
      <v-img
        src="imagen.jpeg" 
        alt="imagen"
        class="imagenProceso"
      >
      </v-img>
    </div>
    
    <div class="procesoDiseño d-flex flex-column align-center">
      <h2 class="text-h4">Diseño</h2>
      <v-img src="diseño.jpeg" alt="" class="imagenProceso">
      </v-img>
    </div>
    
    <div class="procesoProducto d-flex flex-column align-center">
      <h2 class="text-h4">Producto</h2>
      <v-img src="producto.jpeg" alt="" class="imagenProceso">
      </v-img>
    </div>

    <v-divider class="dividerEquipo"></v-divider>

    <div class="equipo">
      <h1 class="text-h3">Nuestro Equipo</h1>
      <div class="flex-row flex-wrap justify-space-around">

        <div class="flex-column">

          <h2 class="text-h4">Ian</h2>
          <v-img src="holaa.jpg" class="imagenProceso">
          </v-img>
        </div>
       
        <div class="flex-column">

          <h2 class="text-h4">Cito</h2>
          <v-img src="ian.png" class="imagenProceso">
          </v-img>
        </div>
      </div>
    </div>

  </v-container>  
</template>

<script>
export default {
  name: 'IndexPagina',
  layout: 'DefaultLayout',
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

.intro {
  grid-area: intro;
  flex-direction: column;
  flex: 1 1 0px;
}

.imagenIntro {
  max-width: 95vw;
}

.textoIntro {
  margin: 1rem auto;
  text-align: center;
  font-size: 2rem !important;
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
  max-width: 300px;
  border-radius: 50%;
}

.dividerEquipo {
  margin: 1rem;
  grid-area: dividerEquipo;
}

.equipo {
  grid-area: equipo;
}

.contenedor {
  align-items: center;
  text-align: center;
  display: grid;
  grid-template-areas:
    "intro"
    "dividerProceso"
    "procesoTitulo"
    "procesoImagen"
    "procesoDiseño"
    "procesoProducto"
    "dividerEquipo"
    "equipo";
}

@media (min-width: 900px) {
  .contenedor {
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-areas:
      "intro          intro          intro         "
      "dividerProceso dividerProceso dividerProceso"
      "procesoTitulo procesoTitulo procesoTitulo"
      "procesoImagen procesoDiseño procesoProducto"
      "dividerEquipo dividerEquipo dividerEquipo"
      "equipo        equipo        equipo       ";
  }

  .intro {
    flex-direction: row;
  }

  .imagenIntro {
    margin: 3rem;
    max-width: 40%;
  }

  .textoIntro {
    margin: 2rem auto;
    font-size: 3.75rem !important;
  }

  .botonPedido {
    padding: 2rem;
  }

  .imagenProceso {
    max-width: 20vw;
  }

  .equipo {
    flex-direction: row;
  }

}
</style>
