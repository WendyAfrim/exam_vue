<script setup>

const props = defineProps({
  as: {
    type: String, 
    required: true
  }, 

  name: {
    type: String,
    required: true
  }, 

  modelValue: {
    type: String
  }
})




</script>

<template>

  <component :is="as" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)">
    <slot></slot>
  </component>

</template>
