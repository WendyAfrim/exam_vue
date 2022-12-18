<script setup>
import FormikVue from "./components/FormikVue.vue";
import FieldVue from "./components/FieldVue.vue";
import Captcha from "./components/Captcha.vue";

const initialValues = { email: "test@test.com", password: "azerty" };
const options = [
  {
    id: 1,
    src: "https://picsum.photos/50?random=1",
  },
  {
    id: 2,
    src: "https://picsum.photos/50?random=2",
  },
  {
    id: 3,
    src: "https://picsum.photos/50?random=3",
  },
  {
    id: 4,
    src: "https://picsum.photos/50?random=4",
  },
  {
    id: 5,
    src: "https://picsum.photos/50?random=5",
  },
  {
    id: 6,
    src: "https://picsum.photos/50?random=6",
  },
  {
    id: 7,
    src: "https://picsum.photos/50?random=7",
  },
  {
    id: 8,
    src: "https://picsum.photos/50?random=8",
  },
  {
    id: 9,
    src: "https://picsum.photos/50?random=9",
  },
];
/* METHODS */

function validate(values) {
  const errors = {};
  if (!values.email) {
    errors.email = "Required";
  } else if (!/^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i.test(values.email)) {
    errors.email = "Invalid email address";
  }
  return errors;
}

function onSubmit(values, { setSubmitting }) {
  setTimeout(() => {
    alert(JSON.stringify(values, null, 2));
    setSubmitting(false);
  }, 400);
}
</script>

<template>
  <FormikVue
    :initialValues="initialValues"
    :validate="validate"
    @submit="onSubmit"
    #default="{ isSubmitting, handleSubmit, values, errors }"
  >
    <h1>Values</h1>
    {{ JSON.stringify(values) }}
    <h1>Errors</h1>
    {{ JSON.stringify(errors) }}
    <br />
    <br />
    <label for="name">Name</label>
    <FieldVue name="name" id="name" /><br />

    <label for="email">Email</label>
    <FieldVue name="email" id="email" /> <br />

    <label for="password">Password</label>
    <FieldVue name="password" id="password" /> <br />

    <label for="password">Color</label>
    <FieldVue name="color" as="select">
      <option value="red">Red</option>
      <option value="green">Green</option>
      <option value="blue">Blue</option>
    </FieldVue>
    <br />

    <FieldVue name="captcha" :options="options" :as="Captcha" />
    <br />
    <button type="submit" @click="handleSubmit" :disabled="isSubmitting">
      Submit
    </button>
  </FormikVue>
</template>

<style scoped></style>
