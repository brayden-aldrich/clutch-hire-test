<!-- Submission Form for the application. Contains all inputs and logic surrounding
 the form itself. -->

<template>
  <h1>Have us reach out</h1>
  <form id="submit-form">
    <fieldset>
      <legend>First Name</legend>
      <input v-model="firstName" class="input-submission" type="text" />
    </fieldset>
    <fieldset>
      <legend>Last Name</legend>
      <input v-model="lastName" class="input-submission" type="text" />
    </fieldset>
    <fieldset>
      <legend>Email</legend>
      <input v-model="email" class="input-submission" type="text" />
    </fieldset>
    <fieldset>
      <legend>Phone Number</legend>
      <input v-model="phone" class="input-submission" type="text" />
    </fieldset>
    <fieldset>
      <legend>Company</legend>
      <input v-model="company" class="input-submission" type="text" />
    </fieldset>
    <button type="button" @click="handleClick">Continue</button>
  </form>
</template>

<style>
h1 {
  font-style: "Roboto";
  align-self: flex-start;
  font-weight: 400;
  width: 310px;
  left: 0;
  font-size: 25px;
  color: #555552;
  margin-bottom: 18.04px;
}

button {
  color: #ffffff;
  background-color: #0b476c;
  text-align: center;
  align-self: flex-end;
  padding-top: 10.22px;
  padding-right: 37.5px;
  padding-left: 37.5px;
  padding-bottom: 8.61px;
  border-radius: 4px;
  margin-top: 51.61px;
  border: none;
}

fieldset {
  border-radius: 3.6px;
  width: 310px;
  max-width: none;
  box-sizing: border-box;
  height: 40.32px;
  border-width: 0.72px;
  border-color: #555552;
  margin-bottom: 23.05px;
  padding: 0 10px;
}

legend {
  font-family: "ABeeZee";
  font-weight: 400;
  font-size: 12px;
  padding-top: 1.26px;
  padding-right: 6.32px;
  padding-left: 6.32px;
  margin-left: 13.07px;
  color: #006315;
}

input {
  width: 100%;
  box-sizing: border-box;
  border: none;
  font-family: "ABeeZee";
  font-size: 15px;
  padding-left: 19.39px;
  margin: 0;
  color: #555552;
}

input:focus {
  outline: none;
  box-shadow: none;
}

#submit-form {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
}
</style>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "SubmitForm",
  data() {
    return {
      firstName: "",
      lastName: "",
      email: "",
      phone: "",
      company: "",
    };
  },
  methods: {
    handleClick() {
      console.log({
        firstName: this.firstName,
        lastName: this.lastName,
        email: this.email,
        phone: this.phone,
        company: this.company,
      });
    },
  },
});
</script>
