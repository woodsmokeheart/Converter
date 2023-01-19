<template>
  <div class="home">
    <CurrencyConverter />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import CurrencyConverter from "@/components/CurrencyConverter.vue";

export default defineComponent({
  name: "AboutView",
  components: {
    CurrencyConverter,
  },
});
</script>
