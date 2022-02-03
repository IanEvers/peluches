<template>
  <v-app>
    <v-app-bar
      app
      color="#52a73c"
      flat
    >
      <v-app-bar-nav-icon class="d-lg-none nav-icon" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

      <v-img
        class="imagen"
        contain
        lazy-src="logo.png"
        max-height="40"
        max-width="150"
        src="logo.png"
      ></v-img>
      <h3 class="adminHeader">ADMIN</h3>
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      app
    >
      <v-sheet
        color="grey lighten-4"
        class="pa-4"
      >
        <v-avatar
          class="mb-4"
          color="grey darken-1"
          size="64"
        ></v-avatar>

        <div>john@vuetifyjs.com</div>
      </v-sheet>

      <v-divider></v-divider>

      <v-list>
        <v-list-item
          v-for="[icon, text] in links"
          :key="icon"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ text }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main class="grey lighten-3">
      <v-container>
        <v-row>
          <Nuxt />
        </v-row>
      </v-container>
    </v-main>

    <v-footer
      color="#52a73c"
      padless
    >
      <v-row
        justify="center"
        no-gutters
      >
        <v-col
          class="lighten-2 py-4 text-center white--text"
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
    name: 'AdminLayout',
    data: () => ({
      drawer: null,
      links: [
        ['mdi-inbox-arrow-down', 'Trabajos por realizar'],
        ['mdi-archive', 'Trabajos realizados'],
        ['mdi-newspaper', 'Novedades'],
        ['mdi-view-dashboard', 'Dashboard general'],
      ],
    }),
}
</script>

<style>
.adminHeader { 
  padding: 1rem;
  margin-left: auto;
}


</style>
