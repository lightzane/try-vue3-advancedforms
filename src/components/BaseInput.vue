<template>
  <!-- 
    * MultiRoot ! 
    * since this template contains 2 child element 
    * and passing `$attrs` will make vue confused 

    * So manually bind the $attrs like so:
    * v-bind = '$attrs'
  -->
    <label>{{ label }}</label>
    <input
      v-bind="$attrs"
      :placeholder="label"
      :value="modelValue"
      @input="$emit('update:modelValue', ($event.currentTarget as HTMLInputElement).value)"
      class="field"
    >
</template>

<script setup lang="ts">
    type Props = {
        label?: string
        modelValue?: string | number // ! `modelValue` is defined and passed by v-model from parent
    }

    const { label = '', modelValue = '' } = defineProps<Props>()
</script>