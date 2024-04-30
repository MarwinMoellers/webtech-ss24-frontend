<script setup lang="ts">
import type { Pizza } from '@/model';

const pizzen: Pizza[] = [
  {name: 'Margarita', price: 10},
  {name: 'Salami', price: 12},
  {name: 'Tonno', price: 14},
]
</script>

<template>
  <h1>Pizza Übersicht</h1>
  <div v-for="pizza in pizzen" :key="pizza.name">
    <div>Pizza: {{pizza.name}}</div>
    <div>Preis: {{pizza.price}}€</div>
  </div>

</template>

<style scoped>

</style>