<script setup lang="ts">
import { supabase } from "../supabase";
import Card from "../components/card.vue";
console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code

// const { data: maisons, error } = await supabase.from("Maison").select("*");
// console.log("maisons",maisons)

// const ou let ?
let { data: maisons, error } = await supabase
  .from('Maison')
  .select('*')

console.log("Maison:", maisons);

// const user = ref(supabase.auth.user());
// supabase.auth.onAuthStateChange(() => {
//     user.value = supabase.auth.user()
// })
</script>

<template>
  <div class="p-2">
    <h1 class="text-2xl">Page Liste Supabase</h1>
    <div  v-for="Maison in maisons" :key="Maison.nomMaison">
      <Card v-bind="Maison"  />
    </div>
  </div>
    
  
  <!-- {{ maisons }} -->
</template>
