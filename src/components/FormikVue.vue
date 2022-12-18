<script setup>
import { provide, reactive, ref } from "vue";

const emit = defineEmits(["submit"]);

const props = defineProps({
  initialValues: {
    type: Object,
    required: true,
  },
  validate: {
    type: Function,
  },
});

const formValues = reactive({ ...props.initialValues });
let formErrors = reactive({});
const isSubmitting = ref(false);

const formik = {
  initialValues: props.initialValues,
  onChange: ({ target: { name, value } }) => {
    formValues[name] = value;
  },
  formValues: formValues,
};
provide("formik", formik);

/* METHODS */

function setSubmitting(val) {
  isSubmitting.value = val;
}

function handleSubmit(e) {
  e.preventDefault();
  setSubmitting(true);
  if (props.validate) formErrors = props.validate({ ...formValues });
  emit("submit", { ...formValues }, { setSubmitting });
}
</script>

<template>
  <div>
    <slot
      :handleSubmit="handleSubmit"
      :isSubmitting="isSubmitting"
      :values="formValues"
      :errors="formErrors"
    ></slot>
  </div>
</template>

<style scoped></style>
