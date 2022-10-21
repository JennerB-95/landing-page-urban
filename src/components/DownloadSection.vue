<template>
  <section class="pb-8" id="download">
    <br/>
    <br/>
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row justify="center">
            <v-col cols="12" sm="12">
              <h1 class="font-weight-light display-1">Tasas por derecho de llave</h1>
              <h3 class="font-weight-light mt-3">
                Las personas que obtengan por primera vez un contrato de arrendamiento, deberán previamente y por única vez, hacer efectivo el pago correspondiente al derecho de llave. Para el efecto se establecen las siguientes tasas:
              </h3>
              <template>
                <v-simple-table>
                  <template v-slot:default>
                    <thead>
                      <tr>
                        <th class="text-left">
                          No.
                        </th>
                        <th class="text-left">
                          Descripción
                        </th>
                        <th class="text-left">
                          Tasa
                        </th>
                      </tr>
                    </thead>
                    <tbody>
                      <tr
                        v-for="item in desserts"
                        :key="item.no"
                      >
                        <td>{{ item.no }}</td>
                        <td>{{ item.name }}</td>
                        <td>{{ item.calories }}</td>
                      </tr>
                    </tbody>
                  </template>
                </v-simple-table>
              </template>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
      <br/>
      <br/>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row justify="center">
            <v-col cols="12" sm="12">
              <template>
                <h1 class="font-weight-light display-1">Tasas de arrendamiento</h1>
              <h3 class="font-weight-light mt-3">
                Sin perjuicio de las tasas establecidas en el Plan de Tasas, Rentas, Multas y demás tributos para el Municipio de Tejutla, se establecen las siguientes rentas:              
              </h3>
                <v-simple-table>
                  <template v-slot:default>
                    <thead>
                      <tr>
                        <th class="text-left">
                          No.
                        </th>
                        <th class="text-left">
                          Descripción
                        </th>
                        <th class="text-left">
                          Numeración de Locales
                        </th>
                        <th class="text-left">
                          Tasa
                        </th>
                      </tr>
                    </thead>
                    <tbody>
                      <tr
                        v-for="item in tasas"
                        :key="item.no"
                      >
                        <td>{{ item.no }}</td>
                        <td>{{ item.name }}</td>
                        <td>{{ item.num }}</td>
                        <td>{{ item.calories }}</td>
                      </tr>
                    </tbody>
                  </template>
                </v-simple-table>
              </template>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
    
    
  </section>
</template>

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

<script>
// import {db} from '@/main'

import Q from 'q';

export default {
  data: () => ({
    desserts: [
          {
            no: "01",
            name: 'Locales (Parque central, Mercado Municipal No. 1 y Edificio de Tres Niveles, Terminal de Autobuses)',
            calories: "Q.500.00",
          },
          {
            no: "02",
            name: 'Casetas',
            calories: "Q.200.00",
          },
          {
            no: "03",
            name: 'Puestos',
            calories: "Q.100.00",
          },
          {
            no: "04",
            name: 'Ventas Móviles',
            calories: "Q.100.00",
          },

        ],
        tasas: [
          {
            no: "01",
            name: 'Locales del Parque Central.',
            num: 'Del Local No. 01 al Local No. 05.',
            calories: "Q.224.00",
          },
          {
            no: "02",
            name: 'Locales frente a ACREDICOM',
            num: 'Del Local No. 01 al Local No. 05.',
            calories: "Q.224.00",
          },
          {
            no: "03",
            name: 'Local a un costado de Juzgado de Paz',
            num: 'Local. No. 6',
            calories: "Q.168.00",
          },
          {
            no: "04",
            name: 'Casetas ubicadas sobre la Tercera Avenida. (Contiguo a Juzgado de Paz y Liceo Belga Tejutleco)',
            num: 'Caseta No. 01 a la Caseta No. 05',
            calories: "Q.112.00",
          },
          {
            no: "05",
            name: 'Locales Mercado Municipal No. 01 (Exteriores)',
            num: 'Del Local No. 01 al Local No. 02',
            calories: "Q.450.00",
          },
          {
            no: "06",
            name: 'Locales Mercado Municipal No. 01 (Interiores)',
            num: 'Del Local No. 04 al Local No. 31',
            calories: "Q.112.00",
          },
          {
            no: "07",
            name: 'Locales Mercado Municipal No. 01 (Exteriores)',
            num: 'Del Local No. 32 al Local No. 43 y Locales No. 45 y No. 46',
            calories: "Q.224.00",
          },
          {
            no: "08",
            name: 'Locales Mercado Municipal No. 01 (Exterior)',
            num: 'Local No. 44',
            calories: "Q.336.00",
          },
          {
            no: "09",
            name: 'Locales Mercado Municipal No. 01',
            num: 'Área de piso de Plaza ',
            calories: "Q.2.00 p/yarda",
          },
          {
            no: "10",
            name: 'Locales Edificio de Tres Niveles, Terminal de Autobuses. Ala Sur. (Exteriores)',
            num: 'Del Local No 01 al Local No. 10',
            calories: "Q.450.00",
          },
          {
            no: "11",
            name: 'Locales Edificio de Tres Niveles, Terminal de Autobuses. Ala Norte. (Exteriores)',
            num: 'Locales No. 11 y 12',
            calories: "Q.300.00",
          },
          {
            no: "12",
            name: 'Locales Edificio de Tres Niveles, Terminal de Autobuses. Ala Norte. (Exteriores)',
            num: 'Del Local No. 13 al Local No. 17',
            calories: "Q.450.00",
          },
          {
            no: "13",
            name: 'Locales Edificio de Tres Niveles, Terminal de Autobuses. (Primer Nivel, Interiores)',
            num: 'Del Local No. 101 al Local No. 110 y del Local No. 169 al Local No. 172',
            calories: "Q.200.00",
          },
          {
            no: "14",
            name: 'Locales Edificio de Tres Niveles, Terminal de Autobuses. (Primer Nivel, Interiores)',
            num: 'Del Local No. 161 al Local No. 164',
            calories: "Q.180.00",
          },
          {
            no: "15",
            name: 'Locales Edificio de Tres Niveles, Terminal de Autobuses. (Primer Nivel, Interiores)',
            num: 'Del Local No. 165 al Local No. 168 y Local No. 173',
            calories: "Q.300.00",
          },
          {
            no: "16",
            name: 'Puestos, Edificio de Tres Niveles, Terminal de Autobuses. (Primer Nivel, Mesones Interiores)',
            num: 'Del Puesto No. 112 al puesto No. 160',
            calories: "Q.180.00",
          },
          {
            no: "17",
            name: 'Locales para carnicerías, Edificio de Tres Niveles, Terminal de Autobuses. (Segundo Nivel, Interiores)',
            num: 'Del Local No. 201 al Local No. 233',
            calories: "Q.300.00",
          },
          {
            no: "18",
            name: 'Locales Edificio de Tres Niveles, Terminal de Autobuses. (Segundo Nivel, Interiores)',
            num: 'Del Local No. 234 al Local No. 249 y del Local No. 264 al Local No. 280',
            calories: "Q.250.00",
          },
          {
            no: "19",
            name: 'Locales Edificio de Tres Niveles, Terminal de Autobuses. (Segundo Nivel, Interiores)',
            num: 'Del Local No. 250 al Local No. 263',
            calories: "Q.300.00",
          },
          {
            no: "20",
            name: 'Locales de Comedores, Edificio de Tres Niveles, Terminal de Autobuses. Ala Sur (Tercer Nivel, Interiores)',
            num: 'Del Local No. 301 al Local No. 317',
            calories: "Q.300.00",
          },
          {
            no: "21",
            name: 'Espacios para Comedores, Edificio de Tres Niveles, Terminal de Autobuses. Ala Sur, Frente a Locales de Comedores. (Tercer Nivel, Interiores)',
            num: 'Del Local No. 318 al Local No. 326',
            calories: "Q.150.00",
          },
          {
            no: "22",
            name: 'Locales Contiguos al Palacio Municipal',
            num: 'Local No. 04 y Local No. 05',
            calories: "Q.450.00",
          },
          {
            no: "23",
            name: 'Local exterior debajo del acceso al Segundo Nivel Edificio de Tres Niveles, Terminal de Autobuses. (Frente a carriles de estacionamiento)',
            num: 'Local No. 326',
            calories: "Q.200.00",
          },
          {
            no: "24",
            name: 'Por piso de plaza, en días especiales y épocas de feria',
            num: 'Calles y avenidas del Municipio',
            calories: "Q.30.00 p/metro cuadrado",
          },
          {
            no: "25",
            name: 'Ventas Móviles en el Corredor del Mercado Municipal No. 01',
            num: 'Venta Móvil No. 5, 9, 15',
            calories: "Q.80.00",
          },
          {
            no: "26",
            name: 'Ventas Móviles en el Corredor del Mercado Municipal No. 01 y frente el Centro de Salud',
            num: 'Venta Móvil No. 3 y 4. Mercado Municipal No. 01. Venta Móvil sin numeración frente al Centro de Salud',
            calories: "Q.120.00",
          },
          {
            no: "27",
            name: 'Ventas Móviles en el Corredor del Mercado Municipal No. 01',
            num: 'Venta Móvil No. 6 y 7',
            calories: "Q.140.00",
          },
          {
            no: "28",
            name: 'Venta Móvil en Corredor del Mercado No. 01',
            num: 'Venta Móvil No. 8',
            calories: "Q.200.00",
          },
          {
            no: "29",
            name: 'Arrendamiento de servicios sanitarios municipales ubicados en Mercado Municipal No. 01',
            num: 'Local No. 3  Mercado Municipal No. 01',
            calories: "Q.700.00 mensual",
          },
          {
            no: "30",
            name: 'Arrendamiento de Servicios sanitarios municipales, ubicados Edificio de Tres Niveles, Terminal de Autobuses',
            num: 'Local No. 111 Edificio de Tres Niveles, Terminal de Autobuses',
            calories: "Q.1,000.00 mensual",
          },
        ],
    icons: ["fa-facebook", "fa-twitter", "fa-linkedin", "fa-instagram"],
    valid: true,
    name: "",
    nameRules: [
      (v) => !!v || "O campo nome é obrigatório",
      (v) => (v && v.length >= 6) || "O nome precisa ter mais de 6 caracteres",
    ],
    email: "",
    emailRules: [
      (v) => !!v || "O campo email é obrigatório",
      (v) => /.+@.+\..+/.test(v) || "O E-mail precisa ser válido",
    ],
    textArea: "",
    textAreaRules: [
      (v) => !!v || "O campo de texto é obrigatório",
      (v) => (v && v.length >= 10) || "Mínimo de 10 caracteres",
    ],
    lazy: false,
    snackbar: {
      enabled: false,
      text: '',
      color: ''
    }
  }),
  methods: {
    submit() {
      /*db.collection("contactData").add({
        name: this.name,
        email: this.email,
        message: this.textArea
      }).then(() => {
        this.snackbar.text = "Mensagem enviada com sucesso"
        this.snackbar.color = "success"
        this.snackbar.enabled = true
      }).catch(() => {
        this.snackbar.text = "Erro ao enviar mensagem"
        this.snackbar.color = "danger"
        this.snackbar.enabled = true
      })*/
    }
  }
};
</script>
