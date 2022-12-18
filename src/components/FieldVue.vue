<script setup>
import { inject } from "vue";

const formik = inject("formik");
defineProps({
  as: {
    type: [String, Object],
    required: false,
    default: "input",
  },

  name: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <component
    :name="name"
    :is="as"
    :value="formik.initialValues[name]"
    @input="formik.onChange"
  >
    <slot></slot>
  </component>
</template>
