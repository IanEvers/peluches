<template>
  <v-container fluid class="grey lighten-5 contenedor">

    <h3 class="text-center">Elegí tu peluche</h3>
    <div class="listaArticulos">

      <articulo-card
        v-for="{nombre, descripcion, precio, proximamente} in articulos"
        :key="nombre"
        :nombre="nombre"
        :descripcion="descripcion" 
        :precio="precio"
        :proximamente="proximamente"
      >
      </articulo-card>
    </div>

  </v-container>
</template>

<script>
import articuloCard from '~/components/articuloCard.vue'
export default {
  name: 'ProductosPage',
  components: { articuloCard },
  data: () => ({
    articulos: [
      {
        nombre: "Dibujo",
        descripcion: "hacemos un peluche en base a un dibujo que nos mandes! Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis, nemo architecto!", 
        precio: 5000,
      },
      {
        nombre: "Foto de tu Mascota",
        descripcion: "hacemos un peluche en base a una foto de tu mascota! Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis, nemo architecto!", 
        precio: 5000
      },
      {
        nombre: "Rompecabezas",
        descripcion: "hacemos un Rompecabezas! Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis, nemo architecto!", 
        precio: 5000,
        proximamente: true
      },
    ]
  })
 }
</script>

<style scoped>
  .listaArticulos {
    display: flex;
    flex-direction: column;
  }

  @media (min-width: 960px) {
    .listaArticulos {
      flex-direction: row;
      flex-wrap: wrap;
    }
  }

</style>