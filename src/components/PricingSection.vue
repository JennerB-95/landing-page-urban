<template>
  <section class="pb-8" id="pricing">
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row justify="center">
            <v-col cols="12" sm="5">
              <h1 class="font-weight-light display-1">Consulta de arrendamientos</h1>
              <h3 class="font-weight-light mt-3">
                Acá puedes consultar el detalle de tu arrendamiento municipal.
              </h3>
              <h3 class="font-weight-light mt-3">
                Cualquier consulta puedes comunicarte.
              </h3>
              <h3 class="font-weight-light mt-3">
                Teléfono: 7760-0140
              </h3>
              <h3 class="font-weight-light">
                Correo: info@munidetejutla.gob.gt
              </h3>
            </v-col>
            <v-col cols="12" sm="7">
              <v-form ref="form" v-model="valid" :lazy-validation="lazy">
                <v-text-field
                    color="#00911A"
                    v-model="name"
                    :rules="nameRules"
                    label="DPI"
                    required
                ></v-text-field>
                <v-btn
                    :disabled="!valid"
                    color="#00911A"
                    :dark="valid"
                    rounded
                    block
                    class="mt-3"
                    @click="submit()"
                >
                  Consultar
                </v-btn>
              </v-form>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
    <div class="svg-border-waves text-white">
      <v-img src="~@/assets/img/borderWavesBlue.svg"/>
    </div>
    <v-snackbar
        v-model="snackbar.enabled"
        timeout="3000"
        right
        top
        :color="snackbar.color"
    >
      {{ snackbar.text }}

      <template v-slot:action="{ attrs }">
        <v-btn
            text
            v-bind="attrs"
            @click="snackbar.enabled = false"
        >
          Fechar
        </v-btn>
      </template>
    </v-snackbar>
    <v-dialog
      v-model="dialog"
      hide-overlay
      persistent
      width="300"
    >
      <v-card
        color="primary"
        dark
      >
        <v-card-text>
          Cargando...
          <v-progress-linear
            indeterminate
            color="white"
            class="mb-0"
          ></v-progress-linear>
        </v-card-text>
      </v-card>
    </v-dialog>
    <div class="text-center">
    <v-dialog
      v-model="dialog2"
      width="700"
    > 
      <v-card>
        <v-card-title class=" grey lighten-2">
          Información de arrendamientos
        </v-card-title>

      <div v-if="dataVecino.length>=1">
        <v-list-item> 
          <v-list-item-content>
            <v-list-item-title> <div class="title">{{vecinoName}}</div> </v-list-item-title>
            <v-list-item-subtitle> <div class="subtitle-1">{{vecinoApellido}}</div> </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item> 
      </div>
      <div v-else class="ma-4">
        <v-alert
          icon="mdi-account-details"
          prominent
          text
          type="info"
        >
        Información no encontrada
        </v-alert>
      </div>
      <div class="">
        <v-expansion-panels focusable flat>
          <v-expansion-panel>
            <v-expansion-panel-header>
              Arrendamientos
            </v-expansion-panel-header>
            <v-expansion-panel-content>
              <div class="mt-3" v-if="leasesVecino.length==0">
                <v-alert
                  icon="mdi-account-details"
                  prominent
                  text
                  type="info"
                >
                  ¡No cuenta con arrendamiento!
                </v-alert>
              </div>
              <div class="ma-3" v-else>
                <v-simple-table>
                  <template v-slot:default>
                    <thead>
                      <tr>
                        <th class="text-left body-2">
                          Tipo de arrendamiento
                        </th>
                        <th class="text-left body-2">
                          Fecha de creación
                        </th>
                        <th class="text-left body-2">
                          Destino
                        </th>
                        <th class="text-left body-2">
                          Fecha de inicio
                        </th>
                        <th class="text-left body-2">
                          Fecha fin
                        </th>
                      </tr>
                    </thead>
                    <tbody>
                      <tr
                        v-for="item in leasesVecino"
                        :key="item.id"
                      >
                        <td>{{ fixTypeLease(item.type_lease) }}</td>
                        <td>{{ fixDateAndHour(item.date_creation) }}</td>
                        <td>{{ item.destiny }}</td>
                        <td>{{ fixDateAndHour(item.initial_date) }}</td>
                        <td>{{ fixDateAndHour(item.final_date) }}</td>

                      </tr>
                    </tbody>
                  </template>
                </v-simple-table>
              </div>
            </v-expansion-panel-content>
          </v-expansion-panel>
          <v-expansion-panel>
            <v-expansion-panel-header>
              Pagos
            </v-expansion-panel-header>
            <v-expansion-panel-content>
              <div class="mt-3" v-if="paymentsVecino.length==0">
                <v-alert
                  icon="mdi-account-details"
                  prominent
                  text
                  type="info"
                >
                  ¡No ha realizado ningún pago!
                </v-alert>
              </div>

              <div class="ma-3" v-else>
                <v-simple-table>
                  <template v-slot:default>
                    <thead>
                      <tr> 
                        <th class="text-left body-2">
                          Fecha de creación
                        </th>
                        <th class="text-left body-2">
                          Descripción
                        </th>
                        <th class="text-left body-2">
                          Total
                        </th>
                        
                      </tr>
                    </thead>
                    <tbody>
                      <tr
                        v-for="item in paymentsVecino"
                        :key="item.id"
                      >
                        <td>{{ fixDateAndHour(item.date_creation) }}</td>
                        <td>{{ item.description }}</td>
                        <td>Q{{ item.total }}</td> 

                      </tr>
                    </tbody>
                  </template>
                </v-simple-table>
              </div>
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
      </div>
      <div class="ma-5 font-weight-medium title">Derecho de llave</div>
 
        <div class="mt-3" v-if="rightKeysVecino.length==0">
          <v-alert
            icon="mdi-key-chain-variant"
            prominent
            text
            type="warning"
          >
            ¡No tiene derecho de llave!
          </v-alert>
        </div>
        
 
      <div v-else>
        <v-alert
          icon="mdi-key-chain-variant"
          prominent
          text
          type="success"
        >
          ¡Ya cuenta con derecho de llave!
        </v-alert>
      </div>  
      <v-divider></v-divider> 
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            text
            @click="dialog2 = false"
            class="ma-3"
          >
            Aceptar
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
  </section>
  
</template>


<script>
// import {db} from '@/main'
import axios from "axios";
import { API } from "../globalVars"; 

export default {
  data () {
      return {
      icons: ["fa-facebook", "fa-twitter", "fa-linkedin", "fa-instagram"],
      valid: true,
      name: "",
      nameRules: [
        (v) => !!v || "DPI es requerido",
        (v) => (v && v.length == 13) || "Ingrese un registro de 13 números",
      ],
      lazy: false,
      snackbar: {
        enabled: false,
        text: '',
        color: ''
      },
       dialog: false,
       dialog2: false,
       vecinoName: "",
       vecinoApellido: "",
       dataVecino: [],
       leasesVecino: [],
       paymentsVecino: [],
       rightKeysVecino: [],

    }

  },

  watch: {
      dialog (val) {
        if (!val) return 
        setTimeout(() => (this.dialog = false), 4000)
      },
    },

  methods: {
    submit() {
      console.log(this.name);
      this.dialog = true
      axios.get(`${API}core/custom-n/?dpi=${this.name}`).then((r)=>{
        this.dataVecino = r.data; 
        this.vecinoName = this.dataVecino[0].names;
        this.vecinoApellido = this.dataVecino[0].surnames; 
        this.leasesVecino = r.data[0].leases;
        this.paymentsVecino = r.data[0].payments;
        this.rightKeysVecino = r.data[0].payments; 
        console.log(r.data, "data");    
        console.log(this.leasesVecino, "arre");
        console.log(this.paymentsVecino, "pagos");
        console.log(this.rightKeysVecino, "llaves");

        setTimeout(() => (this.dialog2 = true), 5000)
      })
    },

    fixDateAndHour(d) {
      let result = new Date(d).toLocaleString();
      return result.substring(0,16) + " hrs";
    },


    fixTypeLease(t) {
      let lease = "";
      switch (t) {
        case 0:
          lease = "Arrendamiento anual";
          break;
        
          case 1:
            lease = "Arrendamiento ocasional";
        default:
          break;
      }
      return lease;
    },
    
  }
};
</script>

<style scoped>
#contact {
  background-color: #f4f7f5;
}

.svg-border-waves .v-image {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 3rem;
  width: 100%;
  overflow: hidden;
}

</style>