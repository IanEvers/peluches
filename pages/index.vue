<template>
  <v-container fluid class="grey lighten-5 contenedor">
    <div class="intro d-flex align-center">

      <v-img src="peluches.png" alt="peluches" class="imagenIntro">
      </v-img>
      <div class="textoIntro">
        <h1>
          mandas una foto, 
          <br>
          recibís un peluche
        </h1>
        <NuxtLink to="pedido">
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

    <v-divider class="dividerEquipo"></v-divider>

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
  font-size: clamp(1.2rem,1rem + 3.5vw);
  text-align: center;
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
    margin: 5rem;
    max-width: 40%;
  }

  .textoIntro {
    margin: 2rem auto;
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
