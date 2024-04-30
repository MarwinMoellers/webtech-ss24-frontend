<script setup lang="ts">
import type { Pizza } from '@/model/model';

const model = defineModel<Pizza[]>()
</script>

<template>
  <div v-for="pizza in model" :key="pizza.name">
    <div>Pizza: {{ pizza.name }}</div>
    <div>Preis: {{ pizza.price }}€</div>
  </div>
</template>

<style scoped>

</style>