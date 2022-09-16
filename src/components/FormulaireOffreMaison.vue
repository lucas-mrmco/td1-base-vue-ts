<script setup lang="ts">
    import { ref } from "@vue/reactivity" ;
    import Card from "./card.vue";
    
   
    //On fait une variable réactive qui réference les donnée
    // ATTENTIONfaire une Ref pas une Reactive car
    // c'est l'objet qui doit être réactif, pas ses props
    const maison = ref({});
</script>

<template>
    <div>
        <div class="p-2">
            <h2 class="text-2xl">Résultat (Prévisualisation) </h2>
    <!--  0ptionnel on affiche les données -->
            <Card v-bind="maison" />
        </div>
        <div class="p-2'">
    <!-- On passe la "ref" à FormKit -->
            <FormKit type="form" v-model="maison" >
            <FormKit name="nom" label="nom" />
            <FormKit name="price" label="prix" type="number"/>
            <FormKit name="favori" label="mettre en valeur"
            type="checkbox" />
            </FormKit>
        </div>
    </div>
</template>