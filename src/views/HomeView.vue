<style>
h1 {
  font-style: "Roboto";
  font-weight: 400;
  font-size: 25px;
  color: #555552;
}

p {
  font-family: "ABeeZee";
  font-weight: 400;
  font-size: 12px;
  color: #006315;
}

button {
  color: #ffffff;
  background-color: #0b476c;
  text-align: center;
  justify-content: center;
  padding-top: 10.22px;
  padding-right: 37.5px;
  padding-left: 37.5px;
  padding-bottom: 8.61px;
  border-radius: 4px;
  border: none;
}

.input-submission {
  border-radius: 3.6px;
  width: 310px;
  height: 40.32px;
  left: 35.76px;
  border-width: 0.72px;
  border-color: #555552;
}
</style>

<template>
  <div class="home">
    <h1>Have us reach out</h1>

    <form id="submit-form">
      <div>
        <p>First Name</p>
        <input class="input-submission" type="text" />
        <p>Last Name</p>
        <input class="input-submission" type="text" />
        <p>Email</p>
        <input class="input-submission" type="text" />
        <p>Phone Number</p>
        <input class="input-submission" type="text" />
        <p>Company</p>
        <input class="input-submission" type="text" />
      </div>
      <button type="submit">Continue</button>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "HomeView",
});
</script>
