<template>
  <v-container fluid class="grey lighten-5 contenedorContacto">
    <h1 class="titulo">Contacto</h1>
    <v-divider class="dividerInicial"></v-divider>
    
    <div class="flex-column redes">
      <p>Nuestras redes:</p>
      <v-btn
        v-for="red in redes" 
        :key="red.nombre"
        :color="red.color"
        :aria-label="red.nombre"
        class="mr-2"
        dark
      >
        <a target="_blank" :href="red.url" class="inherit">
          <v-icon>mdi-{{red.nombre}}</v-icon>
          {{red.descripcion}}
        </a>
      </v-btn>
    </div>
    
    <v-divider class="divider"></v-divider>
    
    <div class="formulario">
      <p>
        Tenés alguna duda? Alguna idea? Algún pedido? Querés diseñar peluches? Mandanos un mail y lo contestamos en el día.
      </p>
      <v-form
        ref="form"
        v-model="valid"
        lazy-validation
      >
        <v-text-field
          v-model="Nombre"
          :rules="NombreRules"
          label="Nombre"
          required
        ></v-text-field>

        <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required
        ></v-text-field>

        <v-textarea
          v-model="mensaje"
          auto-grow
          color="primary"
          label="Mensaje"
          :rules="mensajeRules"
        ></v-textarea>
     
        <v-btn
          :disabled="!valid"
          color="primary"
          class="mt-4"
          @click="enviarMail"
        >
          Enviar
        </v-btn>
      </v-form>
    </div>
  </v-container>
</template>

<script>
export default {
  name: 'ContactoPagina',
  
  data: () => ({
    redes: [
      {
        nombre: 'instagram',
        url: '',
        color: 'purple',
        descripcion: 'Instagram'
      },
      {
        nombre: 'twitter',
        url: '',
        color: 'light-blue',
        descripcion: 'Twitter',
      },
    ],
    valid: true,
    Nombre: '',
    NombreRules: [
      v => !!v || 'el nombre es obligatorio',
    ],
    email: '',
    emailRules: [
      v => !!v || 'el E-mail es obligatorio',
      v => /.+@.+\..+/.test(v) || 'el mail no es válido',
    ],
    mensaje: '',
    mensajeRules: [
      v => !!v || 'El mensaje no puede estar vacío',
    ],
    
  }),
  head() {
    return {
      title: 'Contacto',
      meta: [
        {
          hid: 'Contacto',
          name: 'Contacto',
          content: 'Contacto.'
        }
      ]
    }
  },
  methods: {
    enviarMail () {
      
    },
  },
  
}
</script>

<style scoped>
.titulo {
  grid-area: titulo;
}

.dividerInicial {
  margin-bottom: 1rem;
  grid-area: dividerInicial;
}

.formulario {
  grid-area: formulario;
  max-width: 500px;  
}

.redes {
  grid-area: redes;
}

.divider {
  margin: 1rem;
  grid-area: divider;
}

.contenedorContacto {
  max-width: 800px;
  display: grid;
  grid-template-columns: 1fr;
  grid-template-areas:
    "titulo"
    "dividerInicial"
    "formulario"
    "divider"
    "redes";
}

@media (min-width: 900px) {

}
</style>