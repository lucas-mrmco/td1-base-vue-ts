<script setup lang="ts">
    defineProps<{
        id?: string;
    }>();
    import groupBy from "lodash/groupBy";

    </script>


    <template>
        <FormKit type="form">
            <RouterLink
                :to="{
                    name: 'quartier-id',
                    params: { id: quartierObject.code_Quartier },
                }"
                >{{ quartierObject.libelle_Quartier }}
        </RouterLink>
        </FormKit>
    </template>