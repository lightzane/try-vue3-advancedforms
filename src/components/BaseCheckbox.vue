<template>
    <input
        type="checkbox"
        v-model="model"
        class="field"
    />
    <label v-if="label">{{ label }}</label>
</template>

<script setup lang="ts">
    type Props = {
        label?: string
    }

    const {
        label = ''
    } = defineProps<Props>()

    const model = defineModel()
</script>