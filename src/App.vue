<script setup>
  import { RouterLink, RouterView } from "vue-router";
  import FormikVue from "./components/Formik.vue";
  import FieldVue from "./components/Field.vue";

  let modelValue = '';
  function formSubmit(event) {
      console.log(modelValue)

  }


</script>

<template>
  <FormikVue>
    
      <form action="" @submit.prevent="formSubmit">
        <label for="name">Name</label>
        <FieldVue name="name" id="name" as="input" v-model="modelValue"/>

        <label for="email">Email</label>
        <FieldVue name="email" id="email" as="input" v-model="modelValue"/>

        <label for="password">Password</label>
        <FieldVue name="password" id="password" as="input" />

        <!-- <label for="password">Color</label>
        <FieldVue name="color" as="select">
            <option value="red">Red</option>
            <option value="green">Green</option>
            <option value="blue">Blue</option>
        </FieldVue> -->
        
        <button type="submit">Submit</button>
      </form>
  </FormikVue>
</template>

<style scoped>

</style>
