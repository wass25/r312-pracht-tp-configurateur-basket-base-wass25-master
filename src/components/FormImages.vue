<script setup lang="ts">

import type { Chaussure } from '@/types-images';
import { couleursNoms } from '@/types-images';
import { ref } from 'vue';
import Images from "./Images.vue";
import { TabGroup, TabList, Tab, TabPanels, TabPanel } from "@headlessui/vue";


const chaussure = ref<Chaussure>({});

</script>

<template>
    <div>
        <TabGroup>
            <TabList class="tabs flex gap-1">
                <Tab class="tab tab-lifted ui-selected:tab-active">Coté</Tab>
                <Tab class="tab tab-lifted ui-selected:tab-active">Dessus</Tab>
                <Tab class="tab tab-lifted ui-selected:tab-active">Derriere</Tab>
            </TabList>
            <TabPanels class="w-64 p-2">
                <TabPanel>
                    <Images v-bind="chaussure" class="w-full" />
                </TabPanel>
                <TabPanel>
                    <Images v-bind="chaussure" class="w-full" orientation="dessus" />
                </TabPanel>
                <TabPanel>
                    <Images v-bind="chaussure" class="w-full" orientation="derriere" />
                </TabPanel>
            </TabPanels>
        </TabGroup>

        <FormKit type="form" v-model="chaussure">

            <FormKit type="select" name="bandes" label="Bandes" :options="['bleu']"
                placeholder="Sélectionné une couleur de bandes" />
            <FormKit type="select" name="cuir" label="Cuir" :options="['bleu', 'vert']"
                placeholder="Sélectionné une couleur de cuir" />
            <FormKit type="select" name="mousse" label="Mousse" :options="['bleu', 'vert']"
                placeholder="Sélectionné une couleur de mousse" />

        </FormKit>

    </div>
</template>