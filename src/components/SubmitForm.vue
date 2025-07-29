<!-- Submission Form for the application. Contains all inputs and logic surrounding
 the form itself. -->

<template>
  <h1>Have us reach out</h1>
  <form id="submit-form" @click="clearError()">
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
      <input v-model="email" class="input-submission" type="email" />
    </fieldset>
    <fieldset>
      <legend>Phone Number</legend>
      <input
        v-model="phone"
        @input="formatPhone"
        class="input-submission"
        type="tel"
      />
    </fieldset>
    <fieldset>
      <legend>Company</legend>
      <input v-model="company" class="input-submission" type="text" />
    </fieldset>

    <!-- Error dialogue -->
    <div v-if="error">
      <p class="error-message">
        <strong>Missing or incorrect field(s):</strong>
        <span>
          ({{
            errorMessages.length
              ? errorMessages.join(", ")
              : "Please fill all fields correctly."
          }})
        </span>
      </p>
    </div>

    <!-- Show loader on click and disable button, else just show "Continue" text -->
    <button type="submit" :disabled="submitting" @click.stop.prevent="submit()">
      <div class="button-content">
        <span v-if="submitting" class="loader"></span>
        <span v-else>Continue</span>
      </div>
    </button>
  </form>
</template>

<style>
.error-message {
  position: absolute;
  top: 545px;
  width: 100%;
  color: red;
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
  width: 131px;
  height: 34.83px;
  padding: 0 37.5px;
  border-radius: 4px;
  margin-top: 51.61px;
  border: none;
}

button:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.button-content {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 24px;
  width: 100%;
}

.loader {
  width: 24px;
  height: 24px;
  border: 5px solid #fff;
  border-bottom-color: transparent;
  border-radius: 50%;
  display: inline-block;
  box-sizing: border-box;
  animation: rotation 1s linear infinite;
}

@keyframes rotation {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
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
import { defineComponent, ref } from "vue";
import { useRouter } from "vue-router";

// Clean up the phone number, then check if it's valid based on its length
const cleanPhoneAndValidate = (phone: string) => {
  // get rid of non numeric characters
  const cleaned = phone.replace(/[^0-9]/g, "");
  return {
    valid: cleaned.length >= 9,
    number: cleaned,
  };
};

// main component function
export default defineComponent({
  name: "SubmitForm",
  setup() {
    const router = useRouter();
    const apikey = process.env.VUE_APP_SUBMISSION_API_KEY; //.env.local

    const error = ref(false);
    const errorMessages = ref<string[]>([]); // lists errors from post request

    /** Form variables */
    const firstName = ref("");
    const lastName = ref("");
    const email = ref("");
    const phone = ref("");
    const company = ref("");

    const submitting = ref(false);

    const callError = () => {
      error.value = true;
    };

    const clearError = () => {
      error.value = false;
      errorMessages.value = [];
    };

    // Format phone while typing
    const formatPhone = () => {
      let digits = cleanPhoneAndValidate(phone.value).number;

      if (digits.length > 0) {
        let formatted = "";
        digits = digits.substring(0, 10);

        if (digits.length <= 3) {
          formatted = `(${digits})`;
        } else if (digits.length <= 6) {
          formatted = `(${digits.slice(0, 3)}) ${digits.slice(3)}`;
        } else {
          formatted = `(${digits.slice(0, 3)}) ${digits.slice(
            3,
            6
          )}-${digits.slice(6)}`;
        }
        phone.value = formatted;
      }
    };

    // Main form submission function.
    const submit = async () => {
      clearError(); // reset all error values (error, errorMessages)

      submitting.value = true;
      let cleanNumberObj = cleanPhoneAndValidate(phone.value);
      if (
        !(
          firstName.value &&
          lastName.value &&
          email.value &&
          cleanNumberObj.valid &&
          company.value
        )
      ) {
        submitting.value = false;
        callError();
        return;
      }

      // Make request using .env key
      const req = await fetch(
        `https://dev-api-api.hiring-test.experientialpreview.com/api/lead/${apikey}`,
        {
          method: "POST",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify({
            first: firstName.value,
            last: lastName.value,
            company: company.value,
            phone: cleanNumberObj.number,
            email: email.value,
          }),
        }
      );

      if (req.ok) {
        submitting.value = false;
        router.push("/submitted");
      } else {
        // grab the error objects on the response and display
        const resp = await req.json();

        type APIError = { property: string }; // to avoid using "any" on the foreach
        resp["errors"].forEach((e: APIError) => {
          errorMessages.value.push(e.property);
        });

        callError();
        submitting.value = false;
        return;
      }
    };

    return {
      error,
      errorMessages,
      firstName,
      lastName,
      email,
      phone,
      company,
      submitting,
      callError,
      clearError,
      formatPhone,
      submit,
    };
  },
});
</script>
