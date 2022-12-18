<template>
           <Formik  
           initialValues={{ email: '', password: '' }}       validate={values => {
         const errors = {};
         if (!values.email) {
           errors.email = 'Required';
         } else if (
           !/^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i.test(values.email)
         ) {
           errors.email = 'Invalid email address';
         }
         return errors;
       }}
       @submit={(values, { setSubmitting }) => {
         setTimeout(() => {
           alert(JSON.stringify(values, null, 2));
           setSubmitting(false);
         }, 400);
       }}
       #default="{ isSubmitting, handleSubmit, values, errors }"
     >           <h1>Values</h1>           {{ JSON.stringify(values) }}
           <h1>Errors</h1>           {{ JSON.stringify(errors) }}
           <Field type="email" name="email" />           
           <Field name="captcha" :as="Captcha"/> <!-- Component Captcha -->           
           <img src="xxxxxx" @click="handleSubmit"/>     
        </Formik>
    </template>
