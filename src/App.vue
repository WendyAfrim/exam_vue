<script setup>
  import { RouterLink, RouterView } from "vue-router";
  import FormikVue from "./components/Formik.vue";
  import FieldVue from "./components/Field.vue";


</script>

<template>
  <FormikVue initialValues="" onSubmit="" validate="">
    
      <form action="">
        <label for="name">Name</label>
        <FieldVue name="name" id="name" as="input" />

        <label for="email">Email</label>
        <FieldVue name="email" id="email" as="input"/>

        <label for="password">Password</label>
        <FieldVue name="password" id="password" as="input" />

        <label for="password">Color</label>
        <FieldVue name="color" as="select">
            <option value="red">Red</option>
            <option value="green">Green</option>
            <option value="blue">Blue</option>
        </FieldVue>
        
        <button type="submit">Submit</button>
      </form>
  </FormikVue>

  

</template>

<style scoped>

</style>
