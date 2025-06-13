<template>
  <!-- 
    * MultiRoot ! 
    * since this template contains 2 child element 
    * and passing `$attrs` will make vue confused 

    * So manually bind the $attrs like so:
    * v-bind = '$attrs'
  -->

  <!-- 
    Prior to 3.4
    :value="modelValue"

    Starting 3.4
    v-model="model" (see more comments below)
  -->
    <label>{{ label }}</label>
    <input
      v-bind="$attrs"
      :placeholder="label"
      v-model="model"
      @input="$emit('update:modelValue', ($event.currentTarget as HTMLInputElement).value)"
      class="field"
    >
</template>

<script setup lang="ts">
  /* 
    Prior to Vue 3.4 --

    ! `modelValue` is defined and passed by v-model from parent
    For the parent to listen to event changes use the following like so:

    @input = $emit('update:modelValue', $event.currentTarget.value)

    It is IMPORTANT to use the exact string `update:modelValue` 
    Since this is "v-model" from the parent is listening to
    
    Reference: https://vuejs.org/guide/components/v-model.html#under-the-hood
  */

  /* 
    Starting Vue 3.4 --
    
    We can now use "defineModel()" as macro 
    But we can still use the longer syntax as it is used under the hood by the defineModel()
    
    Reference: https://vuejs.org/guide/components/v-model.html#basic-usage
  */

    type Props = {
        label?: string

        // prior to 3.4
        // modelValue?: string | number // ! `modelValue` is defined and passed by v-model from parent
    }

    const { 
      label = '', 
      // modelValue = '' // prior to 3.4
    } = defineProps<Props>()

    // Starting Vue 3.4 -- v-model from parent will be passed here
    const model = defineModel({ default: '' })
</script>