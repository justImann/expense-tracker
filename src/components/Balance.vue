<template>
  <div>
    <h1 id="balance">${{ total }}</h1>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});
</script>

<style lang=""></style>
