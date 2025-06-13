<template>
    <input
        type="radio"
        v-model="model"
        :value="value"
        v-bind="$attrs"
        />
    <label v-if="label">{{ label }}</label>
</template>

<script setup lang="ts">
type Props = {
    label?: string
    value: string | number
}

const { label = '' } = defineProps<Props>()

const model = defineModel<string | number>()
</script>