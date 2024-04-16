<template>
    <v-app-bar
      scroll-behavior="elevate fade-image"
      scroll-threshold="1000"
      image="https://picsum.photos/1920/1080?random"
    >
      <v-app-bar-nav-icon icon="mdi-dumbbell" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
  
      <v-app-bar-title>Derma fitness zone</v-app-bar-title>
  
      <v-spacer></v-spacer>
  
      <v-btn icon="mdi-cart-heart">
      </v-btn>   
      <v-btn icon="mdi-cart-outline">
      </v-btn>   
      <v-btn icon="mdi-menu-down-outline">
      </v-btn>    
    </v-app-bar>
  
    <v-navigation-drawer v-model="drawer" app>
      <!-- Aquí puedes agregar los elementos de tu menú -->
      <v-list-item title="My Application" subtitle="Vuetify"></v-list-item>
  <v-divider></v-divider>
  <v-list-item link title="List Item 1"></v-list-item>
  <v-list-item link title="List Item 2"></v-list-item>
  <v-list-item link title="List Item 3"></v-list-item>
    </v-navigation-drawer>
  </template>
  

  <script setup>
        import { ref, onMounted } from 'vue'
        import axios from "axios";

        // reactive state
        const drawer = ref(false)

        // functions that mutate state and trigger updates
         async function getBusiness() {

                const options = {
                  method: 'GET',
                  url: 'http://localhost:1337/api/businesses',
                  params: {populate: '*'},
               
                };

                axios.request(options).then(function (response) {
                  console.log(response.data);
                  
                }).catch(function (error) {
                  console.error(error);
                });
        }

        // lifecycle hooks
        onMounted(() => {
            getBusiness()
        })


</script>

