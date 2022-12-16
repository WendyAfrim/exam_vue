<script setup>

  const props = defineProps({
    initialValues: {
      type: Object,
      required: true,
    },
    onSubmit: {
      type: Function,
      required: true,
    },
    validate: {
      type: Function,
      required: true
    }
  });

  const isSubmitting = ref(false);
  const errors = ref([]);

  const handleSubmit = defineEmits({
    "onSubmit": function(values) {
        isSubmitting.value = true;
        errors.value = validate(values);
        isSubmitting.value = false;
    }
  });

</script>

<template>
    <slot @submit.prevent.stop="onSubmit" 
    v-bind:isSubmitting="isSubmitting" 
    v-bind:errors="errors" 
    v-bind:handleSubmit="handleSubmit" 
    :initialValues="initialValues" ></slot>
</template>

<style scoped>
</style>
