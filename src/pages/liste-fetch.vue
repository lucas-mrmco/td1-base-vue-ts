<script setup lang="ts">
import card from "../components/card.vue";
//import maisons from "/maisons.json";

const res = await fetch("/maisons.json");
const maisons = await res.json();
</script>
<template>
    <h1 class="text-2xl">Page Liste Fetch</h1>
  <card v-for="maison in maisons" v-bind="maison" :key="maison.nom" />
  {{ maisons }}
</template>
