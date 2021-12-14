<template>
  <div id="app">
    <Form @submit="onSubmit">
      <h1>Vee Validate PoC</h1>
      <div class="form-control">
        <label for="first-name"> First Name </label>
        <Field
          name="first-name"
          type="text"
          id="first-name"
          :rules="validateFirstName"
        />
        <ErrorMessage name="first-name" />
      </div>
      <div class="form-control">
        <label for="last-name"> Last Name </label>
        <Field
          name="last-name"
          type="text"
          id="last-name"
          :rules="validateLastName"
        />
        <ErrorMessage name="last-name" />
      </div>
      <div class="form-control">
        <label for="email">Please enter a valid email</label>
        <Field name="email" type="email" id="email" :rules="validateEmail" />
        <ErrorMessage name="email" />
      </div>
      <div class="form-control">
        <label for="password">Please enter a valid password</label>
        <Field
          name="password"
          type="password"
          id="password"
          :rules="validatePassword"
        />
        <ErrorMessage name="password" />
      </div>
      <button>Submit form</button>
      <p v-if="success">YOU'VE SUBMITTED THE FORM!</p>
    </Form>
  </div>
</template>
<script>
import { Form, Field, ErrorMessage } from "vee-validate";
export default {
  components: {
    Form,
    Field,
    ErrorMessage,
  },
  data: function () {
    return {
      success: false,
    };
  },
  methods: {
    onSubmit(values) {
      console.log(JSON.stringify(values, null, 2));
      this.success = true;
    },
    validateFirstName(value) {
      if (!value) {
        return "This field is required";
      } else {
        return true;
      }
    },
    validateLastName(value) {
      if (!value) {
        return "This field is required";
      } else {
        return true;
      }
    },
    validateEmail(value) {
      // if the field is empty
      if (!value) {
        return "This field is required";
      }
      // if the field is not a valid email
      const regex = /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i;
      if (!regex.test(value)) {
        return "This field must be a valid email";
      }
      // All is good
      return true;
    },
    validatePassword(value) {
      if (!value) {
        return "This field is required";
      }
      if (value.length < 8) {
        return "Please enter a password with 8 or more charecters";
      }
      return true;
    },
  },
};
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-content: center;
}
.form-control > * {
  display: block;
  margin-bottom: 12px;
}
span {
  color: red;
}
p {
  font-size: 20px;
  font-weight: bold;
  color: green;
}
</style>
