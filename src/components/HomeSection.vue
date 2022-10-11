<template>
  <section id="hero">
    <v-parallax contain dark src="@/assets/img/muni.jpg" height="750">
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row align="center" justify="center">
            <v-col cols="12" md="6" xl="8">
              <h1 class="display-2 font-weight-bold mb-4">Municipalidad de Tejutla</h1>
              <h1 class="font-weight-light">
                Un municipio bendecido por Dios
              </h1>
              <div class="video d-flex align-center py-4">
              </div>
            </v-col>
            <v-col cols="12" md="6" xl="4" class="hidden-sm-and-down"> </v-col>
          </v-row>
        </v-col>
      </v-row>
      <div class="svg-border-waves text-white">
        <v-img src="@/assets/img/borderWaves.svg" />
      </div>
    </v-parallax>
    <v-container fluid id="features" class="mt-2">
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row align="center" justify="space-around">
            <!-- <v-col cols="12" class="text-center">
              <h1 class="font-weight-light display-2">Title</h1>
              <h1 class="font-weight-light">
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
              </h1>
            </v-col> -->
            <v-col
              cols="12"
              sm="4"
              class="text-center"
              key="1"
            >
              <v-hover v-slot:default="{ hover }">
                <v-card
                  class="card"
                  shaped
                  :elevation="hover ? 10 : 4"
                  :class="{ up: hover }"
                >
                <v-img
                    src="@/assets/img/vision.png"
                    max-width="100px"
                    class="d-block ml-auto mr-auto"
                    :class="{ 'zoom-efect': hover }"
                  ></v-img>

                  <h1 class="font-weight-regular">Visión</h1>
                  <h4 class="font-weight-regular subtitle-1">
                    Somos una entidad autónoma y descentralizada, al servicio de los habitantes del municipio de Tejutla, tecnológicamente preparada, con personal profesional apropiado para poder afrontar los retos del futuro; desempeñarnos con ética y transparencia y proteger los patrimonios del municipio, velar por el cumplimiento de los planes y programas y atender las necesidades de los vecinos conforme la disponibilidad de recursos.</h4>
                </v-card>
              </v-hover>
            </v-col>
            <v-col
              cols="12"
              sm="4"
              class=""
              key="2"
            >
              <v-hover v-slot:default="{ hover }">
                <v-card
                  class="card"
                  shaped
                  :elevation="hover ? 10 : 4"
                  :class="{ up: hover }"
                >
                 
                <v-img
                    src="@/assets/img/mision.png"
                    max-width="100px"
                    class="d-block ml-auto mr-auto"
                    :class="{ 'zoom-efect': hover }"
                  ></v-img>

                  <h1 class="font-weight-regular text-center">Misión</h1>
                  <h4 class="font-weight-regular subtitle-1 text-center">
                    Servir a las personas de las áreas rurales y urbana del municipio, fortaleciendo los servicios públicos existentes e implementando nuevos donde se carece de ellos, atendiendo las prioridades que las mismas comunidades realizan de acuerdo a sus necesidades y poniendo en práctica métodos de descentralización y fortalecimiento del poder local, para logar la participación comunitaria en la toma de decisiones.
                  </h4>
                  <br/>
                </v-card>
              </v-hover>
            </v-col>
            <v-col
              cols="12"
              sm="4"
              key="3"
            >
              <v-hover v-slot:default="{ hover }">
                <v-card
                  class="card"
                  shaped
                  :elevation="hover ? 10 : 4"
                  :class="{ up: hover }"
                >
                 
                <v-img
                    src="@/assets/img/valor.png"
                    max-width="100px"
                    class="d-block ml-auto mr-auto"
                    :class="{ 'zoom-efect': hover }"
                  ></v-img>
                  <h1 class="font-weight-regular text-center">Principios</h1>
                  <ul style= "list-style-type: square;">
                    <li> <h4 class="font-weight-regular subtitle-1">
                    Honradez y transparencia en el manejo de los recursos                  
                  </h4></li>
                    <li> <h4 class="font-weight-regular subtitle-1">
                    Equidad en las políticas internas y proyección municipal                  
                  </h4> </li>
                    <li> <h4 class="font-weight-regular subtitle-1">
                    Eficiencia y eficacia en la prestación de los servicios
                  </h4> </li>
                    <li> <h4 class="font-weight-regular subtitle-1">
                    Descentralización de los servicios
                  </h4> </li>
                    
                    <li> <h4 class="font-weight-regular subtitle-1">
                    Disciplina en el desempeño del trabajo                  
                  </h4> </li><br/>
                  </ul>
                </v-card>
              </v-hover>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
    <div class="svg-border-waves">
      <img src="~@/assets/img/wave2.svg" />
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
    };
  },
  watch: {
   
  },
  methods: {
    
  },
};
</script>

<style lang="scss">
.circle {
  stroke: white;
  stroke-dasharray: 650;
  stroke-dashoffset: 650;
  -webkit-transition: all 0.5s ease-in-out;
  opacity: 0.3;
}

.playBut {
  /*  border: 1px solid red;*/
  display: inline-block;
  -webkit-transition: all 0.5s ease;

  .triangle {
    -webkit-transition: all 0.7s ease-in-out;
    stroke-dasharray: 240;
    stroke-dashoffset: 480;
    stroke: white;
    transform: translateY(0);
  }

  &:hover {
    .triangle {
      stroke-dashoffset: 0;
      opacity: 1;
      stroke: white;
      animation: nudge 0.7s ease-in-out;

      @keyframes nudge {
        0% {
          transform: translateX(0);
        }
        30% {
          transform: translateX(-5px);
        }
        50% {
          transform: translateX(5px);
        }
        70% {
          transform: translateX(-2px);
        }
        100% {
          transform: translateX(0);
        }
      }
    }

    .circle {
      stroke-dashoffset: 0;
      opacity: 1;
    }
  }
}
</style>

<style>
.btn-play {
  transition: 0.2s;
}

.svg-border-waves .v-image {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 3rem;
  width: 100%;
  overflow: hidden;
}

#hero {
  z-index: 0;
}
.svg-border-waves img {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  margin-bottom: -2px;
  z-index: -1;
}

.card {
  min-height: 300px;
  padding: 10px;
  transition: 0.5s ease-out;
}

.card .v-image {
  margin-bottom: 15px;
  transition: 0.75s;
}

.card h1 {
  margin-bottom: 10px;
}

.zoom-efect {
  transform: scale(1.1);
}

.up {
  transform: translateY(-20px);
  transition: 0.5s ease-out;
}
</style>

<style>
section {
  position: relative;
}
</style>
