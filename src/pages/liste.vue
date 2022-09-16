<template>
    <div class="p-2">
        <h1 class="text-2xl">Page Liste</h1>
        <div v-for="maisons in maisons" :key="maisons.nom">
            <Card class="w-1/2" v-bind="maisons"/>
        </div>
    </div>
    </template>

<script setup lang="ts">
    
import Card from "../components/card.vue";

  const maisons = [{nom:"test", price:60, favoris:true, txt:"produit de test", nbbath:2, nbsize:"test m²", img:"/public/maison1.png"}, {nom:"test2", price:7, favoris:false, txt:"2ème produit de test", nbbath:2, nbsize:"test*2 m²", img:"/public/maison2.png"}, {nom:"Dernier test", price:43, txt:"Dernier produit de test", nbbath:1, nbsize:"test m²", img:"/public/maison3.png"}]
//   import maisons from "../assets/maisons.json";
</script>