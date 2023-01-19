<template>
  <div class="about">
    <ExchangeRates />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import ExchangeRates from "@/components/ExchangeRates.vue";

export default defineComponent({
  name: "HomeView",
  components: {
    ExchangeRates,
  },
});
</script>
