<script setup lang="ts">
    import { ref } from "@vue/reactivity" ;
    import Card from "./card.vue";
    import { supabase } from '@/supabase';
    import { useRouter } from "vue-router";
    
   
    //On fait une variable réactive qui réference les donnée
    // ATTENTIONfaire une Ref pas une Reactive car
    // c'est l'objet qui doit être réactif, pas ses props
    const router = useRouter();
    const maison = ref({});
    
    const props = defineProps(["id"]);
    if (props.id) {
        // On charge les données de la maison
        let { data, error } = await supabase
            .from("Maison")
            .select("*")
            .eq("id", props.id);
        if (error) console.log("n'a pas pu charger le table Maison :", error);
        else maison.value = (data as any[])[0];
    }
    //, favoris: true
    async function upsertMaison(dataForm, node) {
        const { data, error } = await supabase.from("Maison").upsert(dataForm);
        if (error || !data) node.setErrors([error?.message])
        else {
            node.setErrors([]);
            router.push({ name: "edit-id", params: { id: data[0].id } });
        }
    }

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
            <FormKit @submit="upsertMaison" type="form" v-model="maison" 
            :config="{
                classes: {
                    input: 'p-1 rounded border-gray-300 shadow-sm border',
                    label: 'text-gray-600',},
                }"
                :submit-attrs="{ classes: { input: 'bg-red-300 p-1 rounded' }                      
        }">

            <FormKit name="nomMaison" label="Nom de l'annonce" />
            <FormKit name="adresse" label="adressee du bien"/>
            <FormKit name="price" label="Tarif par mois" type="number"/>
            <FormKit name="nbbed" label="Nombre de lits" type="number"/>
            <FormKit name="nbsdb" label="Nombre de salles de bains" type="number"/>
            <FormKit name="superficie" label="Superficie en m²" type="number"/>
            <FormKit name="favoris" label="mettre en valeur"
            type="checkbox" wrapper-class="flex gap-3" />
            </FormKit>
        </div>
    </div>
</template>