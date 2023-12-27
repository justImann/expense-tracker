<template lang="">
  <div>
    <h3>Add new transaction</h3>
    <form id="form" @submit.prevent="onSubmit">
      <div class="form-control">
        <label for="text">Text</label>
        <input
          v-model="text"
          type="text"
          id="text"
          placeholder="Enter text..."
        />
      </div>
      <div class="form-control">
        <label for="amount"
          >Amount <br />
          (negative - expense, positive - income)</label
        >
        <input
          v-model="amount"
          type="text"
          id="amount"
          placeholder="Enter amount..."
        />
      </div>
      <button class="btn">Add transaction</button>
    </form>
  </div>
</template>
<script setup>
import { ref } from "vue";
import { useToast } from "vue-toastification";

const text = ref("");
const amount = ref("");

const toast = useToast();

const emit = defineEmits(["transactionSubmitted"]);

const onSubmit = () => {
  if (!text.value || !amount.value) {
    // Display a toast error message if either field is empty
    toast.error("Both fields must be filled.");
    return;
  }

  const transactionData = {
    text: text.value,
    amount: parseFloat(amount.value),
  };

  emit("transactionSubmitted", transactionData);

  // Clear form fields
  text.value = "";
  amount.value = "";
};

// const onSubmit = () => {
//   if (!text.value || !amount.value) {
//     toast.error("both fields must not empty!");
//   }

//   const transactionData = {
//     text: text.value,
//     amount: parseFloat(amount.value),
//   };

//   console.log(transactionData.text);

//   emit("transactionSubmitted", transactionData);

//   const text = "";
//   const amount = "";
// };
</script>
<style lang=""></style>
