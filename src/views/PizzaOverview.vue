<script setup lang="ts">
import type { Pizza } from '@/model/model';
import { type Ref, ref } from 'vue';

const pizzen: Ref<Pizza[]> = ref([
  { name: 'Margarita', price: 10 },
  { name: 'Salami', price: 12 },
  { name: 'Tonno', price: 14 },
]);

let newPizza: Ref<Pizza> = ref({ name: 'hier name', price: 0 });

function addNewPizza() {
  pizzen.value.push(newPizza.value);
}
</script>

<template>
  <h1>Pizza Übersicht</h1>
  <div v-for="pizza in pizzen" :key="pizza.name">
    <div>Pizza: {{ pizza.name }}</div>
    <div>Preis: {{ pizza.price }}€</div>
  </div>

  <div>
    <label>Pizza Name</label>
    <input type="text" v-model="newPizza.name">
    <label>Pizza Preis</label>
    <input type="number" v-model="newPizza.price">
    <button @click="addNewPizza()">Hinzufügen</button>
  </div>

</template>

<style scoped>

</style>