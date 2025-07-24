<style>
@font-face {
  font-family: "ABeeZee";
  src: url("~/src/assets/fonts/ABeeZee/ABeeZee-Regular.ttf");
}

html,
body {
  height: 100%;
  margin: 0;
}

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

.home {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  width: 310px;
  margin: 0 auto;
}
</style>

<template>
  <div class="home">
    <h1>Have us reach out</h1>
    <form id="submit-form">
      <fieldset>
        <legend>First Name</legend>
        <input class="input-submission" type="text" />
      </fieldset>
      <fieldset>
        <legend>Last Name</legend>
        <input class="input-submission" type="text" />
      </fieldset>
      <fieldset>
        <legend>Email</legend>
        <input class="input-submission" type="text" />
      </fieldset>
      <fieldset>
        <legend>Phone Number</legend>
        <input class="input-submission" type="text" />
      </fieldset>
      <fieldset>
        <legend>Company</legend>
        <input class="input-submission" type="text" />
      </fieldset>
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
