<script setup lang="ts">
    import {
        Disclosure,
        DisclosureButton,
        DisclosurePanel,
    } from '@headlessui/vue';
    import groupBy from "lodash/groupBy";
    import { supabase } from "../../supabase";
    const { data, error } = await supabase.from("quartiercommune").select("*");
    if (error) console.log("n'a pas pu charger la table quartiercommune :", error);
    </script>
    
    <template>
        <section class="flex flex-col">
            <h3 class="text-2xl">Liste des communes</h3>
            <Disclosure v-for="(listeCommune, libelle_Quartier) in groupBy(
              data,
              'libelle_Quartier'
            )" :key="libelle_Quartier">
                <DisclosureButton> {{libelle_Quartier}}</DisclosureButton>
                <DisclosurePanel>
                    <ul>
                        <li v-for="communeObject in listeCommune" :key="communeObject.code_Commune">
    
                            {{ communeObject.libelle_commune }}
                        </li>
                    </ul>
                </DisclosurePanel>
            </Disclosure>
        </section>
    </template>