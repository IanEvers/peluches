<template>

  <v-app>
    <v-app-bar
      app
      color="#52a73c"
      flat
    >
      <v-app-bar-nav-icon class="d-md-none" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      
      <v-img
        class="imagen"
        contain
        lazy-src="logo.png"
        max-height="40"
        max-width="150"
        src="logo.png"
      ></v-img>

      <v-navigation-drawer
        v-model="drawer"
        absolute
        left
        app
        temporary
      >
        <div class="linksSidebar">
          <NuxtLink 
            v-for="link in links" 
            :key="link.nombre" 
            :to="link.link" 
            :style="{color: link.color}"
          >
            {{ link.nombre }}
          </NuxtLink>
        </div>
      </v-navigation-drawer>

      <div class="links">
        <NuxtLink 
          v-for="link in links" 
          :key="link.nombre" 
          :to="link.link" 
          class="d-none d-md-block" 
          style="color: white"
        > 
          {{ link.nombre }}
        </NuxtLink>
      </div>
    </v-app-bar>

    <v-main class="grey lighten-3">
      <v-container>
        <v-row>
          <Nuxt />
        </v-row>
      </v-container>
    </v-main>

    <v-footer
      color="#78cfe0"
      padless
    >
      <v-row
        justify="center"
        no-gutters
      >
      
        <v-col
          class="primary lighten-2 py-4 text-center white--text"
          cols="12"
        >
          {{ new Date().getFullYear() }} — <strong>Peluches</strong>
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    name: 'DefaultLayout',
    data: () => ({
      drawer: false,
      isActive: false,
      links: [
        {
          nombre: 'Inicio',
          link: '/',
          color: 'green'
        },
        {
          nombre: 'Productos',
          link: '',
          color: '#8B1470'
        },
        {
          nombre: 'Precios',
          link: '',
          color: '#ff5733'
        },
        {
          nombre: 'Contacto',
          link: 'contacto',
          color: '#8B6CA1'
        },
        {
          nombre: 'Nuestro Equipo',
          link: 'actividades',
          color: '#1A4E90'
        },
      ],
    }),
  }
</script>

<style>

h2 {
  padding: 1rem;
  font-size: 3rem;
}

.row {
  justify-content: center;
}

a {
  text-decoration: none;
}

.inherit {
  color: inherit !important;
}

.theme--light.v-sheet{
  color: black;
}

.centro {
  display: contents;
}

.links {
  display: flex;
  gap: 2rem;
}

.flex-row {
  display: flex;
}

.linksSidebar {
  display: flex;
  flex-direction: column;
  padding: 1rem;
  gap: 1rem;
}

.v-toolbar__content {
  justify-content: space-evenly;
}

.v-image__image--preload {
  filter: none;
}

.v-lazy {
  display: contents;
}

.col-sm-12 {
  padding: 0;
}
</style>

