<script setup lang="ts">
import type { Pizza } from '@/model/model';
import { type Ref, ref } from 'vue';
import HelpMe from '@/components/HelpMe.vue';
import PizzaListComponent from '@/components/PizzaListComponent.vue';

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
  <PizzaListComponent v-model="pizzen"></PizzaListComponent>


  <div>
    <label>Pizza Name</label>
    <input type="text" v-model="newPizza.name">
    <label>Pizza Preis</label>
    <input type="number" v-model="newPizza.price">
    <button @click="addNewPizza()">Hinzufügen</button>
  </div>

  <HelpMe />

</template>

<style scoped>

</style>