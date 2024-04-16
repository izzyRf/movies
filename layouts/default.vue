<template>
<header>
    <v-card>
        <v-layout>
            <v-app-bar
                    scroll-behavior="elevate fade-image"
                    scroll-threshold="1000"
                    image="https://picsum.photos/1920/1080?random"
            >
                <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>


                <v-app-bar-title>DermaFitness shop</v-app-bar-title>

                <v-spacer></v-spacer>
                <!-- Aquí es donde agregamos el menú desplegable -->
                    <v-menu>
                        <template v-slot:activator="{ props }">
                            <!-- <v-btn
                              color="primary"
                              v-bind="props"
                            >
                              Productos
                            </v-btn> -->
                             <v-btn  v-bind="props" >
                                Productos
                            </v-btn> 
                        </template>
                        <v-list>
                            <v-list-item
                              v-for="(item, index) in business"
                              :key="index"
                              :value="index"
                            >
                                <v-list-item-title>{{ item.attributes.name }}</v-list-item-title>
                            </v-list-item>
                        </v-list>
                    </v-menu>
                    <v-btn icon="mdi-cart-heart">
                    </v-btn>   
                    <v-btn icon="mdi-cart-outline">
                    </v-btn>   
                    <v-btn icon="mdi-menu-down-outline">
                    </v-btn>    
            </v-app-bar>

           <!--  <NuxtPage/> -->
 <slot/>
            <v-navigation-drawer
                v-model="drawer"
                location="bottom"
                temporary
            >
                <v-list>
                    <v-list-item
                        v-for="(item, index) in business"
                        :key="index"
                        :value="index"
                    >
                        <v-list-item-title>{{ item.attributes.name }}</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-navigation-drawer>

        </v-layout>
    </v-card>
</header>
<!-- <div>
    <slot/>
<p>{{ business }}</p>
</div> -->

</template>

<script setup>
    import { ref, watch } from 'vue';
    import axios from "axios";

    const drawer = ref(false);
    const group = ref(null);
    const business = ref(null);
    const items = ref([
        {
            title: 'Suplementos alimenticios',
            value: 'foo',
        },
        {
          title: 'Productos dermatológicos',
          value: 'bar',
        },
        {
          title: 'Accesorios / Moda',
          value: 'fizz',
        }
    ]);

    watch(group, () => {
      drawer.value = false;
    });


    async function getBusiness() {
        const options = {
            method: 'GET',
            url: 'http://localhost:1337/api/businesses',
            params: {populate: '*'},
        };

        const response = axios.request(options).then(function (response) {
           /*  console.log("asi nomas viejo")
            console.log(response.data.data); */
            return response.data.data;
        }).catch(function (error) {
          console.error(error);
        });

       return  response.data !== null ?  response: [] ;


    }

     onMounted(async () => {
            business.value = await getBusiness()
          
            
        })



</script>