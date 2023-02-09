<script setup>
//import TheWelcome from '../components/TheWelcome.vue'
import { useCounterStore } from '@/store/counter.js';
import { storeToRefs } from 'pinia';
const useCounter = useCounterStore()

const { count } = storeToRefs(useCounter);
const { increment } = useCounter;
</script>

<template>
  <main>
    <!-- <TheWelcome /> -->

    <h1>Home Counter: {{ count }}</h1>
    <h2>Double: {{ useCounter.double }}</h2>
    <button @click="increment">Incrementar</button>
  </main>
</template>