
<template>
     <v-container fluid class="mt-16">
    <v-row >
      <!-- <v-col
        v-for="n in 3"
        :key="n"
        cols="12"
        sm="4"
      >
        <v-sheet class="ma-2 pa-2">
          One of three columns
        </v-sheet>
      </v-col> -->
      <v-col cols="12">
        <v-parallax
    src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg"
  >
    <div class="d-flex flex-column fill-height justify-center align-center text-white">
      <h1 class="text-h4 font-weight-thin mb-4">
        DermaFitness Shop
      </h1>
      <h4 class="subheading">
       Construyete a ti mismo, con nuestros mejores productos de cuidado personal
      </h4>
    </div>
  </v-parallax>
      </v-col>
    </v-row>
  </v-container>
</template>