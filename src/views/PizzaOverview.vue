<script setup lang="ts">
import type { Pizza } from '@/model/model';
import { type Ref, ref } from 'vue';
import HelpMe from '@/components/HelpMe.vue';
import PizzaListComponent from '@/components/PizzaListComponent.vue';
import axios from 'axios';

const pizzen: Ref<Pizza[]> = ref([
  { name: 'Margarita', price: 10 },
  { name: 'Salami', price: 12 },
  { name: 'Tonno', price: 14 },
]);

let newPizza: Ref<Pizza> = ref({ name: 'hier name', price: 0 });

function addNewPizza() {
  pizzen.value.push(newPizza.value);
  axios.post(import.meta.env.VITE_BACKEND_URL + '/pizza', newPizza.value)
}

axios.get(import.meta.env.VITE_BACKEND_URL + '/pizza')
    .then(function (response) {
      // handle success
      // console.log("response")
      console.log(response);
      pizzen.value = response.data
    })
    .catch(function (error) {
      // handle error
      console.log(error);
    })
    .finally(function () {
      // always executed
    });

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