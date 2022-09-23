<script setup lang="ts">
import { supabase } from "../supabase";
console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code
const { data: maisons, error } = await supabase.from("Maison").select("*");
console.log("maisons",maisons)
</script>

<template>
    <h1 class="text-2xl">Page Liste Fetch</h1>
  <card v-for="maison in maisons" v-bind="maison" :key="maison.nomMaison" />
  {{ maisons }}
</template>
