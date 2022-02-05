<template>
  <div>
    <v-stepper v-model="pasoActual" non-linear>
      <v-stepper-header>
        <v-stepper-step
          editable
          :complete="pasoActual > 1"
          edit-icon="mdi-check"
          complete-icon="mdi-check"
          step="1"
        >
          <v-icon>mdi-camera</v-icon>
          Fotos
        </v-stepper-step>

        <v-divider></v-divider>

        <v-stepper-step
          editable
          :complete="pasoActual > 2"
          edit-icon="mdi-check"
          complete-icon="mdi-check"
          step="2"
        >
          <v-icon>mdi-lead-pencil</v-icon>
          Datos del Pedido
        </v-stepper-step>

        <v-divider></v-divider>

        <v-stepper-step
          step="3"
        >
          <v-icon>mdi-credit-card-check-outline</v-icon>
          Facturación
        </v-stepper-step>
      </v-stepper-header>

      <v-stepper-items>
        <v-stepper-content step="1">
          <v-btn
            color="primary"
            block
            @click="pasoActual = 2"
          >
            Siguiente
          </v-btn>

        </v-stepper-content>

        <v-stepper-content step="2">

          <div class="formularioAclaraciones">

            <div class="d-flex">
              <v-text-field
                v-model="Nombre"
                :rules="NombreRules"
                label="Nombre"
                required
                class="mr-5"
              ></v-text-field>
              
              <v-text-field
                v-model="apellido"
                :rules="apellidoRules"
                label="Apellido"
                required
              ></v-text-field>
              
            </div>
            
            <v-text-field
              v-model="email"
              :rules="emailRules"
              label="E-mail"
              required
            ></v-text-field>

            <div class="d-flex align-center">
              <v-text-field
                v-model="unit"
                type="number"
                min="1"
                label="Cantidad"
              >
              </v-text-field>
            </div>
            <div class="">
              <v-textarea
                v-model="aclaraciones"
                auto-grow
                color="primary"
                label="Aclaraciones"
              ></v-textarea>
            </div>
          </div>


          <v-btn
            color="primary"
            @click="pedirBotonDeCompra"
          >
            Siguiente
          </v-btn>

          <v-btn 
            text
            @click="pasoActual = 1"
          >
            Atrás
          </v-btn>
        </v-stepper-content>

        <v-stepper-content step="3">

          <div class="d-flex flex-column">

            <p class="text-h4 text-center">Gracias!</p>
            <p class="ml-3"> Abajo tenés el link para pagar con MercadoPago </p>

            <v-divider class="mb-5"></v-divider>

            <v-btn
              v-if="botonUrl == 'loading'"
              max-width="500"
              height="6rem"
              dark
              color="rgb(0, 158, 227)"
              class="ma-auto"
            >
              <div  class="loader">
              </div>
            </v-btn>

            <a v-else :href="botonUrl.url" class="pagarConMercadoPago ma-auto">
              <v-btn
                max-width="500"
                height="6rem"
                dark
                color="rgb(0, 158, 227)"
                class="ma-auto"
              >
                <div v-if="botonUrl == 'loading'" class="loader">
                
                </div>
                  
                  <v-img src="MercadoPago.png" alt="mercadoPago" width="200">
                  </v-img>
              </v-btn>
            </a>
          </div>
        </v-stepper-content>
      </v-stepper-items>
    </v-stepper>

  </div>
</template>

<script>

export default {
  name: 'CheckoutPage',
  data () {
    return {
      pasoActual: 1,
      unit: 1,
      botonUrl: '',
      Nombre: '',
      NombreRules: [
        v => !!v || 'El nombre es obligatorio',
      ],
      apellido: '',
      apellidoRules: [
        v => !!v || 'El apellido es obligatorio',
      ],
      email: '',
      emailRules: [
        v => !!v || 'El E-mail es obligatorio',
        v => /.+@.+\..+/.test(v) || 'el mail no es válido',
      ],
      aclaraciones: '',
    }
  },
  methods: {
    async pedirBotonDeCompra() {
      this.pasoActual = 3
      this.botonUrl = 'loading'
      this.botonUrl = await this.$axios.$post('http://localhost:4000/payment/new', {
        name: this.Nombre,
        apellido: this.apellido,
        unit: this.unit,
        img: 'this.img',
        price: 51,
        email: this.email,
      })
    }
  }
}

</script>

<style>
  a.uppy-Dashboard-poweredBy {
    display: none;
  }

  .uppy-DashboardContent-bar {
    z-index: 0;
  }

  .v-stepper {
    width: 100vw;
  }

  .loader {
    border: 16px solid #f3f3f3; /* Light grey */
    border-top: 16px solid #3498db; /* Blue */
    border-radius: 50%;
    width: 4rem;
    height: 4rem;
    animation: spin 2s linear infinite;
  }

  .pagarConMercadoPago {
    color: white !important;
  }


@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

  @media (min-width: 960px) {
    .v-stepper {
      width: 75vw;
    }
    
   

    .formularioAclaraciones {
      max-width: 800px;
    }
  }
</style>