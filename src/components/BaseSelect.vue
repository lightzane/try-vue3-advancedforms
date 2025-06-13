<template>
  <label v-if="label">{{ label }}</label>
  <!-- 
    ! prior to 3.4
    :value="modelValue"
    v-bind $attrs, and use onChange for (@change)
    v-bind $attrs, and use onInput for (@input)

    * Example
    :value="modelValue"
    v-bind="{
        ...$attrs,
        onChange: ($event) => {
            $emit('update:modelValue', ($event.currentTarget as HTMLSelectElement).value)
        }
    }"

    * Starting Vue 3.4+
    v-model="modelValue" 
  -->
  <select 
    class="field"
    v-model="modelValue"
  >
    <option
      v-for="option in options"
      :value="option"
      :key="option"
      :selected="option === modelValue">
      {{ option }}
    </option>
  </select>
</template>

<script setup lang="ts">
type Props = {
  label?: string;
//   modelValue: string | number // prior to 3.4
  options: string[]
};

const { 
    label = '',
    // modelValue = '' // prior to 3.4
} = defineProps<Props>();

// [Vue 3.4+] Use when single v-model binding
// const modal = defineModel({ default: '' })

// [Vue 3.4+] Use when multiple v-model binding
const modelValue = defineModel<string | number>('modelValue', {
    default: ''
})
</script>
