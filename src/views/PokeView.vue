<script setup>
import axios from "axios";
import { ref } from "vue";
//importar useRoute porque aqui no existe... aunq en el template si existe sin importar
import { useRoute, useRouter } from "vue-router";
import { useGetData } from '@/composables/getData';


const route = useRoute();
const router = useRouter();

const back = () => {
    //lo podemos utilizar para regresar al usuario a la pagina anterior
    router.push("/pokemons");
};

const { data, loading, getData,error } = useGetData();
getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)



/* const pokeSprite = ref({});
    
    const getData = async () => {
    console.log(route.params.name);
    try {
        
        const { data } = await axios.get(
            `https://pokeapi.co/api/v2/pokemon/${route.params.name}`
        );
        pokeSprite.value = data.sprites.front_default;
        console.log(pokeSprite)
    } catch (error) {
        console.log(error);
        pokeSprite.value = null;
    }
};

getData(); */

</script> 

<template>

    <p v-if="loading">Cargando información...</p>
    <div class="alert alert-danger" v-if="error">{{ error }}</div>

    <div v-if="data">
        <img :src="data.sprites?.front_default" alt="" />
        <h1>Poke: {{ $route.params.name }}</h1>
    </div>
    <h1 v-else>Pokemon no encontrado...</h1>
    <button @click="back()" class="btn btn-outline-primary">Volver al listado</button>

</template>