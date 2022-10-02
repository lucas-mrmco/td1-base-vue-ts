<script setup lang="ts">
    import { supabase } from '@/supabase';
    import { useRouter } from "vue-router";

    import groupBy from "lodash/groupBy";
    defineProps<{
        id?: string;
    }>();
   
    async function supprimerQuartier() {
  const { data, error } = await supabase
    .from("Quartier")
    .delete()
    .match({ code_Quartier: quartierObject.value.code_Quartier });
  if (error) {
    console.error(
      "Erreur à la suppression de ",
      quartierObject.value,
      "erreur :",
      error
    );
  } else {
    router.push("/quartier");
  }
}

    </script>


    <template>
            <FormKit name="code_Quartier" label="Quartier" type="select">
                <option value="">Choisir un quartier...</option>
                <optgroup v-for="(listeQuartier, libelle_commune) in groupBy(Quartier,'libelle_commune')" :key="libelle_commune" v-bind:label="libelle_commune">
                    <option v-for="Quartier in listeQuartier" :key="Quartier.id" v-bind:value="Quartier.code_Quartier">{{Quartier.libelle_Quartier}}</option>
                </optgroup>
                
        <button
        type="button"
        v-if="quartierObject.code_Quartier"
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
      </dialog>
            <!-- <RouterLink
                :to="{
                    name: 'quartier-id',
                    params: { id: quartierObject.code_Quartier },
                }"
                >{{ quartierObject.libelle_Quartier }}
        </RouterLink> -->
        </FormKit>
    </template>