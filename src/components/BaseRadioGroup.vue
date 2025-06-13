<template>
    <!-- 
     The <component> varies depending on the ":is"
     for example :is = div, then the <component> renders to <div>
    -->
    <component 
        :is="vertical ? 'div' : 'span'"
        v-for="option of options"
        :key="option.value"
        :class="{
            horizontal: !vertical
        }">
        <BaseRadio
            :label="option.label"
            :value="option.value"
            :name="name"
            v-model="model"
        />
    </component>
    
</template>

<script setup lang="ts">
import BaseRadio from '@/components/BaseRadio.vue';

type OptionType = { label: string, value: string | number }

type Props = {
    name: string
    options: OptionType[]
    vertical?: boolean
}

defineProps<Props>()
const model = defineModel<string | number>()
</script>

<style scoped>
.horizontal {
    margin-right: 20px;
}
</style>