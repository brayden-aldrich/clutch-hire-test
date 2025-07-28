<template>
  <div class="about">
    <GreenTechImg />
    <div class="main-text">
      <h1>Thank you</h1>
      <h1>We will contact you shortly</h1>
    </div>
  </div>
</template>

<style>
.main-text {
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
h1 {
  font-style: "Roboto";
  text-align: center;
  align-self: flex-start;
  font-weight: 400;
  width: 310px;
  left: 0;
  font-size: 25px;
  color: #555552;
  margin-bottom: 18.04px;
}
</style>

<script>
import { defineComponent, onMounted } from "vue";
import { useRouter } from "vue-router";
import GreenTechImg from "@/components/GreenTechImg.vue";

export default defineComponent({
  name: "ThankYouView",
  components: {
    GreenTechImg,
  },
  setup() {
    const router = useRouter();
    // return to submission form after 5 seconds
    onMounted(() => {
      setTimeout(() => {
        router.push("/");
      }, 5000);
    });
  },
});
</script>
