<script setup>
import { useFavoritosStore } from "@/store/favoritos";
import { storeToRefs } from "pinia";
import { RouterLink } from "vue-router";

const useFavoritos = useFavoritosStore();
const { favoritos } = storeToRefs(useFavoritos); // solo para los getters o datos reactivos
const { remove } = useFavoritos; // destructuring directomente de la store

</script>

<template>
    <h1>Favoritos</h1>
    <p v-if="favoritos.length === 0">Sin favoritos</p>
    <ul class="list-group" v-else>
        <li class="list-group-item" v-for="poke in favoritos" :key="poke.id">
            {{ poke.name }}

            <router-link class="btn btn-sm btn-outline-primary me-2" :to="`/pokemons/${poke.name}`">
                Más info
            </router-link>
            <button class="btn btn-sm btn-outline-danger" @click="remove(poke.id)">
                Eliminar
            </button>
        </li>
    </ul>
</template>