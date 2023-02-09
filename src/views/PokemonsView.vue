<script setup>
//import axios from 'axios'
//import { ref } from 'vue';

import { RouterLink } from 'vue-router';
import { useGetData } from '@/composables/getData';

import { useCounterStore } from '@/store/counter.js';
const useCounter = useCounterStore()

const { data, loading, getData, error } = useGetData();
getData('https://pokeapi.co/api/v2/pokemon')


/* const pokemons = ref([]);

const getData = async () => {
    try {
        const { data } = await axios.get('https://pokeapi.co/api/v2/pokemon')
        console.log(data.results)
        pokemons.value = data.results;
    } catch (error) {
        console.log(error)
    }
};
getData(); */

</script>


<template>
    <h1>Home Counter: {{ useCounter.count }}</h1>
    <h2>Double: {{ useCounter.double }}</h2>
    <button @click="useCounter.increment">Incrementar</button>
    
    <h1>Pokemons</h1>
    <p v-if="loading">Cargando información...</p>
    <div class="alert alert-danger" v-if="error">{{ error }}</div>
    <div v-if="data">
        <button :disabled="!data.previous" class="btn btn-success me-2"
            @click="getData(data.previous)">Previous</button>
        <button :disabled="!data.next" class="btn btn-primary" @click="getData(data.next)">Next</button>
        <ul class="list-group">
            <li class="list-group-item" v-for="poke in data.results" :key="poke.id">
                <router-link :to="`/pokemons/${poke.name}`">{{ poke.name }}</router-link>
            </li>
        </ul>
    </div>
</template>