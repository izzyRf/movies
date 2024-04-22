<template>

  <v-container fluid >
    <!-- <v-row  class="mt-14 bg-grey-lighten-5" >
      <v-col
        v-for="product in products"
        :key="product.id"
        xs="12"
        sm="3"
        md="3"
        lg="3"
        xl="2"
        class=" px-1 border-md mt-3 mr-2 ml-2 mb-3 fondo-columna rounded"
      >
      <p class="text-product text-center"> {{product.attributes.name}} </p>
          <v-card
            class="mx-auto mt-4 border-sm"
            elevation="2"
            max-width="270"
            v-if="product.attributes.gallery.data != null"
          >
              <v-carousel  :continuous="false"
                :show-arrows="false"
                delimiter-icon="mdi-square" :height="300" hide-delimiter-background color="#022b3a" 
              >
                <v-carousel-item
                  v-for="photo in product.attributes.gallery.data"
                  :key="photo.id"
                  :src="photo.attributes.url"
                ></v-carousel-item>
              </v-carousel>
          </v-card>
          <v-card
            class="mx-auto mt-4"
            elevation="2"
            max-width="270"
            v-else
          >
              <v-img
                :height="300"
                aspect-ratio="1/1"
                :src=" product.attributes.image.data != null && product.attributes.image.data.attributes.url "
              ></v-img>
          </v-card>

      <div class="text-center">
    
      </div>
      
      <div style="display: flex; justify-content: center; align-items: center; margin-top:10px;">
        <p class="text-price2">Precio:</p>
        <v-chip class="center-text ml-1" prepend-icon="mdi-currency-usd" variant="outlined">
          <p class="text-price">  {{product.attributes.price != null ? product.attributes.price  : 'precio no disponible'}} </p>
        </v-chip>
        <v-chip
          class="ma-2"
          color="green"
          size="small"
          label
          v-if="product.attributes.discount > 0 && product.attributes.discount < 1 "
        >
          <v-icon icon="mdi-percent-circle" start ></v-icon>
         - %{{ product.attributes.discount * 100 }} descuento
        </v-chip>
      </div>
      <div v-if=" product.attributes.rating != null " style="display: flex; justify-content: center; align-items: center; margin-top:-5px;">
          <v-rating
            v-model="product.attributes.rating"
            active-color="#BFDBF7"
            color="#E1E5F2"
            size="small"
          ></v-rating>
      </div>

      <div v-if=" product.attributes.rating != null " class="contenedor">
          <p class="text-description-product">
            {{  product.attributes.description != null ? product.attributes.description :  '' }}
          </p>
      </div>


          <div style="display: flex; justify-content: center; align-items: center;">
          
          <v-btn class="mt-2" append-icon="mdi-cart-plus" variant="outlined" size="small" color="#1F7A8C">
            <p class="text-cart">  Agregar a carrito </p>
          </v-btn>
          </div>

          

      </v-col>
    </v-row> -->

  <v-row class="px-1 ga-1 mt-14 bg-grey-lighten-5 ">
      <v-col
        v-for="product in products"
        :key="product.id"
        xs="12"
        sm="3"
        md="3"
        lg="2"
        xl="2"
        xxl="2"
        class="px-1 border-md p-2 fondo-columna rounded"
      >
      <p class="text-product text-center"> {{product.attributes.name}} </p>
          <v-card
            class="mx-auto mt-4 border-sm"
            elevation="2"
            max-width="270"
            v-if="product.attributes.gallery.data != null"
          >
              <v-carousel  :continuous="false"
                :show-arrows="false"
                delimiter-icon="mdi-square" :height="300" hide-delimiter-background color="#022b3a" 
              >
                <v-carousel-item
                  v-for="photo in product.attributes.gallery.data"
                  :key="photo.id"
                  :src="photo.attributes.url"
                ></v-carousel-item>
              </v-carousel>
          </v-card>
          <v-card
            class="mx-auto mt-4"
            elevation="2"
            max-width="270"
            v-else
          >
              <v-img
                :height="300"
                aspect-ratio="1/1"
                :src=" product.attributes.image.data != null && product.attributes.image.data.attributes.url "
              ></v-img>
          </v-card>

          <!-- <v-chip class="center-text" prepend-icon="mdi-account-tie-hat" variant="outlined">
          <p class="text-price "> {{product.attributes.price != null ?`$${product.attributes.price}`  : 'precio no disponible'}} </p>

      </v-chip> -->
      <div class="text-center">
    
  </div>
      <div style="display: flex; justify-content: center; align-items: center; margin-top:10px;">
        <p class="text-price2">Precio:</p>
        <v-chip class="center-text ml-1" prepend-icon="mdi-currency-usd" variant="outlined">
          <p class="text-price">  {{product.attributes.price != null ? product.attributes.price  : 'precio no disponible'}} </p>
        </v-chip>
        <v-chip
          class="ma-2"
          color="green"
          size="small"
          label
          v-if="product.attributes.discount > 0 && product.attributes.discount < 1 "
        >
          <v-icon icon="mdi-percent-circle" start ></v-icon>
         - %{{ product.attributes.discount * 100 }} descuento
        </v-chip>
      </div>
      <div v-if=" product.attributes.rating != null " style="display: flex; justify-content: center; align-items: center; margin-top:-5px;">
          <v-rating
            v-model="product.attributes.rating"
            active-color="#BFDBF7"
            color="#E1E5F2"
            size="small"
          ></v-rating>
      </div>

      <div v-if=" product.attributes.rating != null " class="contenedor">
          <p class="text-description-product">
            {{  product.attributes.description != null ? product.attributes.description :  '' }}
          </p>
      </div>


          <div style="display: flex; justify-content: center; align-items: center;">
          <!--   <v-text-field
              v-model="piezas"
              type="number"
              :rules="[value => !value || value >= 0 || 'El número debe ser mayor a 0']"
              variant="outlined"
              style="width: 160px; height=10px;"
            >
            <template v-slot:append>
              <v-icon color="#022B3A">
                mdi-plus
              </v-icon>
            </template>
            <template v-slot:prepend>
              <v-icon color="#022B3A">
                mdi-minus
              </v-icon>
            </template>
          </v-text-field> -->
          <v-btn class="mt-2" append-icon="mdi-cart-plus" variant="outlined" size="small" color="#1F7A8C">
            <p class="text-cart">  Agregar a carrito </p>
          </v-btn>
          </div>

          

      </v-col>
  </v-row>
    

    <!-- <v-row>
      <v-col
        cols="12"
      >
      <p>{{products}}</p>
        
      </v-col>
    </v-row> -->
  </v-container>
  
 
</template>


<script setup>
    import { ref, watch } from 'vue';
    import axios from "axios";


    const products = ref(null);
    const rating = ref(3.5);
    const piezas = ref(0);

    




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

<style scoped>

.text-product{
  font-family: 'Jost', sans-serif;
  font-optical-sizing: auto;
  font-weight: '10px';
  font-style: initial;
  text-transform: initial;
  color: #022b3a !important;
  text-align: center;
  font-weight: bold;
  /* Añade las siguientes líneas a tu código */
  white-space: nowrap; /* Evita que el texto se pase a la siguiente línea */
  overflow: hidden; /* Oculta el texto que se sale del contenedor */
  text-overflow: ellipsis; /* Añade puntos suspensivos al final del texto que se sale del contenedor */
}

.text-price{
  font-family: 'Jost', sans-serif;
  font-optical-sizing: auto;
  font-weight: '14px';
  font-style: normal;
  text-transform: initial;
  color: #022b3a !important;
  text-align: center;
  font-weight: bold;
}

 .text-price2{
  font-family: 'Jost', sans-serif;
  font-optical-sizing: auto;
  font-weight: '14px';
  font-style: normal;
  text-transform: initial;
  color: #023a12 !important;
  text-align: center;
}

.text-cart{
  font-family: 'Jost', sans-serif;
  font-optical-sizing: auto;
  font-weight: '11px';
  font-style: normal;
  text-transform: initial;
  color: #022b3a !important;
  text-align: center;
}

.text-description-product{
  font-family: 'Jost', sans-serif;
  font-optical-sizing: auto;
  font-weight: '9px';
  font-style: inherit;
  margin: 12px;
  color: #022b3a !important;
  text-align: justify; 
  
}

.fondo-columna{
  background-color: #FFF !important;
} 

.card-shadow {
  position: relative;
  box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.1);
}

.card-shadow::before {
  content: "";
  position: absolute;
  z-index: -1;
  top: 5px;
  left: 5px;
  right: 5px;
  bottom: 5px;
  box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.1);
}

.contenedor {
  height: 165px; 
  overflow: hidden; 
  line-height: 1.2em; /* Establece la altura de línea */
  max-height: 4.5em; /* Establece la altura máxima a tres líneas de texto */
  margin-top: -15px;
}


</style>