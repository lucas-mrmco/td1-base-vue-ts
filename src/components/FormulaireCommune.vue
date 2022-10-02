<script setup lang="ts">
  import { ref } from "@vue/reactivity";
  import Card from "./card.vue";
  import { supabase } from '@/supabase';
  import { useRouter } from "vue-router";
  
  const router = useRouter();
  const quartier = ref({});
  
  const props = defineProps(["id"]);
  if (props.id) {
      // On charge les données de la maison
      let { data, error } = await supabase
          .from("Commune")
          .select("*")
          .eq("id", props.id);
      if (error) console.log("n'a pas pu charger le table Quartier :", error);
      else quartier.value = (data as any[])[0];
  }
  
  
  
  //, favoris: true
  async function upsertCommune(dataForm, node) {
      const { data, error } = await supabase.from("Commune").upsert(dataForm);
      if (error || !data) node.setErrors([error?.message])
      else {
          node.setErrors([]);
          router.push({ name: "commune-id", params: { id: data[0].id } });
      }
  }
  
  async function supprimerQuartier() {
const { data, error } = await supabase
  .from("Commune")
  .delete()
  .match({ code_Quartier: communeObject.value.code_Commune });
if (error) {
  console.error(
    "Erreur à la suppression de ",
    communeObject.value,
    "erreur :",
    error
  );
} else {
  router.push("/commune");
}
}

  
  
  </script>
  <template>
      <div class="flex flex-row-reverse justify-center">
          <div class="p-2">
              <h2 class="text-2xl">Résultat (Prévisualisation)</h2>
              <Card class="w-3/4 m-auto" v-bind="quartier" />
          </div>
          <div class="p-5">
              <FormKit @submit="upsertCommune" type="form" v-model="commune" :config="{
              classes: {
              input: 'p-1 rounded border-gray-400 shadow-m border',
              label: 'text-gray-800',
              },
              }" :submit-attrs="{ classes: { input: 'bg-red-500 p-2 rounded' } }">
                  <FormKit name="libelle_Quartier" label="La commune/ la ville de la maison" />
              </FormKit>
              <!-- <button
      type="button"
      v-if="communeObject.code_Quartier"
      @click="($refs.dialogSupprimer as any).showModal()"
      class="focus-style justify-self-end rounded-md bg-red-500 p-2 shadow-sm"
    >
      Supprimer l'offre
    </button>
    <dialog
      ref="dialogSupprimer"
      @click="($event.currentTarget as any).close()"
    >
      <button
        type="button"
        class="focus-style justify-self-end rounded-md bg-blue-300 p-2 shadow-sm"
      >
        Annuler</button
      ><button
        type="button"
        @click="supprimerQuartier()"
        class="focus-style rounded-md bg-red-500 p-2 shadow-sm"
      >
        Confirmer suppression
      </button>
  </dialog> -->
          </div>
      </div>
  </template>