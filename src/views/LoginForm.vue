<template>
  <form @submit.prevent="onSubmit">
<<<<<<< HEAD
    <BaseInput v-model="email" label="Email" type="email" :error="emailError" />
=======
    <BaseInput
      label="Email"
      type="email"
      :error="emailError"
      :modelValue="email"
      @change="handleChange"
    />
>>>>>>> L6

    <BaseInput
      v-model="password"
      label="Password"
      type="password"
      :error="passwordError"
    />

    <BaseButton type="submit" class="-fill-gradient"> Submit </BaseButton>
  </form>
</template>

<script setup>
import { useField, useForm } from "vee-validate";
<<<<<<< HEAD

function onSubmit() {
  alert("Submitted");
}

const validations = {
  email: (value) => {
    if (!value) return "The field is required!";

    const regex =
      /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
    if (!regex.test(String(value).toLowerCase())) {
      return "Please enter a valid email address";
    }

    return true;
  },
  password: (value) => {
    const requiredMessage = "This field is required";
    if (value === undefined || value === null) return requiredMessage;
    if (!String(value).length) return requiredMessage;

    return true;
  },
};

useForm({
  validationSchema: validations,
});

const { value: email, errorMessage: emailError } = useField("email");
const { value: password, errorMessage: passwordError } = useField("password");

// option api 寫法
// export default {
//   setup() {
// function onSubmit() {
//   alert("Submitted");
// }

// const { value: email, errorMessage: emailError } = useField(
//   "email",
//   function (value) {
//     if (!value) return "The field is required!";

//     const regex =
//       /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
//     if (!regex.test(String(value).toLowerCase())) {
//       return "Please enter a valid email address";
//     }

//     return true;
//   },
// );

//     return {
//       onSubmit,
//       email: email,
//       emailError: emailError,
//     };
//   },
// };
=======

function onSubmit() {
  alert("Submitted");
}

const validations = {
  email: (value) => {
    if (!value) return "This field is required";

    const regex =
      /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
    if (!regex.test(String(value).toLowerCase())) {
      return "Please enter a valid email address";
    }

    return true;
  },
  password: (value) => {
    const requiredMessage = "This field is required";
    if (value === undefined || value === null) return requiredMessage;
    if (!String(value).length) return requiredMessage;

    return true;
  },
};

const { setFieldValue } = useForm({
  validationSchema: validations,
});

const handleChange = (event) => {
  setFieldValue("email", event.target.value);
};

const { value: email, errorMessage: emailError } = useField("email");

const { value: password, errorMessage: passwordError } = useField("password");
>>>>>>> L6
</script>
