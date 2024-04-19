<template>

  <v-container  fluid >
    <v-row no-gutters class="mt-10">
      <v-col
        v-for="product in products"
        :key="product.id"
        cols="12"
        sm="3"
        class="bg-surface-variant px-1"
      >
      <h4 class="text-blue"> {{product.attributes.name}} n</h4>
          <v-card
            class="mx-auto"
            elevation="24"
            max-width="350"
            v-if="product.attributes.gallery.data != null"
          >
              <v-carousel show-arrows="hover" :height="300" hide-delimiters>
                <v-carousel-item
                  v-for="photo in product.attributes.gallery.data"
                  :key="photo.id"
                  :src="photo.attributes.url"
                  cover
                ></v-carousel-item>
<!-- 
                <v-carousel-item
                  src="https://cdn.vuetifyjs.com/images/cards/hotel.jpg"
                  cover
                ></v-carousel-item>

                <v-carousel-item
                  src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
                  cover
                ></v-carousel-item> -->
              </v-carousel>
          </v-card>
           <v-card
            class="mx-auto"
            elevation="24"
            max-width="350"
            v-else
          >
              <v-img
  :width="272"
  aspect-ratio="1/1"
  cover
  :src="product.attributes.image.data.attributes.url"
></v-img>
          </v-card>

          
      </v-col>
    </v-row>

    <v-row>
         <v-col
       cols="12"
      >
      
        {{products}}
      </v-col>
    </v-row>
  </v-container>
 
</template>


<script setup>
    import { ref, watch } from 'vue';
    import axios from "axios";


    const products = ref(null);



    async function getProducts() {
        const options = {
            method: 'GET',
            url: 'http://localhost:1337/api/products',
            params: {populate: '*'},
        };

        const response = await axios.request(options).then(function (response) {
            return response.data.data;
        }).catch(function (error) {
          console.error(error);
        });
        console.log(response)
       return  response.data !== null ?  response: [] ;


    }

    onMounted(async () => {
            products.value = await getProducts()
    })



</script>
