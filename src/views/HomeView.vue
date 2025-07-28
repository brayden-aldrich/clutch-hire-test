<template>
  <div class="home">
    <GreenTechImg />
    <SubmitForm />
  </div>
</template>

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

<script lang="ts">
import { defineComponent } from "vue";
import GreenTechImg from "@/components/GreenTechImg.vue";
import SubmitForm from "@/components/SubmitForm.vue";

export default defineComponent({
  name: "HomeView",
  components: {
    GreenTechImg,
    SubmitForm,
  },
});
</script>
