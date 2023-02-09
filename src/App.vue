<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <nav class="navbar bg-body-tertiary">
    <div class="container">
      <router-link class="navbar-brand" to="/">
        <img src="@/assets/logo.svg" alt="Bootstrap" width="30" height="24">
        Pokemones API
      </router-link>
      <div>
        <router-link class="btn btn-outline-primary me-2" to="/">Home</router-link>
        <router-link class="btn btn-outline-primary me-2" to="/pokemons">Pokemones</router-link>
        <router-link class="btn btn-outline-primary me-2" to="/about">about</router-link>
      </div>
    </div>
  </nav>

  <div class="container text-center">
    <RouterView />
  </div>
</template>