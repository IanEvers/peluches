<template>
  <v-card
    class="mx-auto ma-2 articuloCard"
    outlined
  >
    <div 
      v-if="proximamente"
      class="proximamente" 
    >
      PRÓXIMAMENTE
    </div>

    <v-list-item class="articulo">
      <v-list-item-content class="pa-1">
        <v-list-item-title class="text-h5 mb-1 ma-5">
          {{nombre}}
        </v-list-item-title>
        <p class="descripcion mt-2">{{descripcion}}</p>
        <h3 class="ml-5 mb-4 hidden-sm-and-down">$ {{precio}}</h3>
      </v-list-item-content>

      <v-img
        src="peluches.png"
        class="articuloImagen"
      ></v-img>
    </v-list-item>

    <v-card-actions class="precioComprar">
      <h3 class="ma-4 hidden-md-and-up">$ {{precio}}</h3>
      <v-btn
        block
        color=#52a73c
        :dark="!proximamente"
        :disabled="proximamente"
        width="90%"
        class="botonComprar"
      >
        Pedir
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: 'ArticuloCard',
  props: {
    nombre: {
      type: String,
      required: true
    },
    descripcion:{
      type: String,
      required: true
    },
    precio: {
      type: Number,
      required: true
    },
    proximamente: {
      type: Boolean,
      default: false
    },
  }
}
</script>

<style scoped>

.articulo {
  display: flex;
  flex-direction: column;
  padding: 0;
  min-height: -webkit-fill-available;
}

.articuloCard {
  max-width: 425px;
}

.descripcion {
  line-height: 1.4;
  padding: 1rem;
}

.articuloImagen {
  max-width: min(90vw, 400px);
}

.precioComprar {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0 !important;
}

.proximamente {
  position: absolute;
  z-index: 4;
  background: black;
  text-align: center;
  color: white;
  width: 100%;
  float: right;
}

@media (min-width: 960px) {
  .articulo {
    flex-direction: row;
  }

  .articuloImagen {
    max-width: 300px;
  }

  .articuloCard {
    max-width: 600px;
  }

  .precioComprar {
    flex-direction: row;
  }
}

</style>