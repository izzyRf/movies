<template>
<header>
    <v-card>
        <v-layout>
            <v-app-bar
                    scroll-behavior="elevate fade-image"
                    scroll-threshold="1000"
                    
                    elevation-1
                    color="#1F7A8C"
            >
                <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>


                <v-app-bar-title>DermaFitness shop</v-app-bar-title>

                <v-spacer></v-spacer>
                <!-- Aquí es donde agregamos el menú desplegable -->
                    <v-menu
                    class="btnText"
                        v-for="(item, index) in business"
                        :key="index"
                        :value="index"
                        
                    >
                        <template v-slot:activator="{ props }">
                            <!-- <v-btn
                              color="primary"
                              v-bind="props"
                            >
                              Productos
                            </v-btn> -->
                             <v-btn class="btnText" v-bind="props" :prepend-icon="item.attributes.icon">
                                
                                <span>{{item.attributes.name}}</span>
                            </v-btn> 
                        </template>
                        <v-list>
                            <v-list-item
                              v-for="(item, index) in item.attributes.categories.data"
                              :key="index"
                              :value="index"
                              append-icon="mdi-account-tie-hat"
                            >
                                <v-list-item-title>{{ item.attributes.name }}</v-list-item-title>
                            </v-list-item>
                        </v-list>
                    </v-menu>
                    <v-btn icon="mdi-cart-heart">
                    </v-btn>   
                    <!-- <v-btn icon="mdi-cart-outline">
                    </v-btn>    -->
                    <v-btn icon="mdi-menu-down-outline">
                        
                    </v-btn>    
            </v-app-bar>

           <!--  <NuxtPage/> -->
 <slot/>
            <v-navigation-drawer
            class="bg-black"
                v-model="drawer"
                location="bottom"
                temporary
            >
                <v-list>
                    <v-list-item
                        v-for="(item, index) in business"
                        :key="index"
                        :value="index"
                        append-icon="mdi-account-tie-hat"
                        rounded
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

        const response = await axios.request(options).then(function (response) {
           /*  console.log("asi nomas viejo")
            console.log(response.data.data); */
            return response.data.data;
        }).catch(function (error) {
          console.error(error);
        });
        console.log(response)
       return  response.data !== null ?  response: [] ;


    }

     onMounted(async () => {
            business.value = await getBusiness()
          
            
        })



</script>



<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Jost:ital,wght@0,100..900;1,100..900&display=swap');

.btnText{
 font-family: 'Jost', sans-serif;
  font-optical-sizing: auto;
  font-weight: '12px';
  font-style: normal;
  text-transform: initial;
  color: #022b3a;

}

.backNavbar{
    background: rgb(2,0,36);
    background: linear-gradient(180deg, rgba(2,0,36,1) 0%, rgba(4,4,29,0.9654062308517157) 21%, rgba(57,123,129,1) 56%, rgba(0,212,255,1) 97%);
}
</style>