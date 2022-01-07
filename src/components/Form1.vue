<template>
  <Form @submit="onSubmit" :validation-schema="schema">
    <h1>Vee Validate PoC</h1>
    <ErrorMessage name="firstName" />
    <ErrorMessage name="lastName" />
    <ErrorMessage name="email" />
    <ErrorMessage name="password" />
    <div class="form-control">
      <label for="first-name"> First Name </label>
      <Field name="firstName" type="text" id="first-name" />
    </div>
    <div class="form-control">
      <label for="last-name"> Last Name </label>
      <Field name="lastName" type="text" id="last-name" />
    </div>
    <div class="form-control">
      <label for="email">Please enter a valid email</label>
      <Field name="email" type="email" id="email" />
    </div>
    <div class="form-control">
      <label for="password">Please enter a valid password</label>
      <Field name="password" type="password" id="password" />
    </div>
    <button type="submit">Submit form</button>
    <p v-if="success">YOU'VE SUBMITTED THE FORM!</p>
  </Form>
</template>
<script>
import { Form, Field, ErrorMessage } from "vee-validate";
import * as yup from "yup";

export default {
  components: {
    Form,
    Field,
    ErrorMessage,
  },
  data() {
    const schema = yup.object({
      firstName: yup.string().required("First name is required"),
      lastName: yup.string().required("Last name is required"),
      email: yup.string().required("Email is required").email(),
      password: yup.string().required("Password is required").min(8),
    });

    return {
      success: false,
      schema,
    };
  },
  methods: {
    onSubmit(values) {
      console.log(JSON.stringify(values, null, 2));
      this.success = true;
    },
  },
};
</script>
