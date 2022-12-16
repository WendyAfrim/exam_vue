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
})

</script>

<template>

  <component :is="as">
    <slot></slot>
  </component>

</template>
