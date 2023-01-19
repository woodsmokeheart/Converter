<template>
  <div>
    <label for="base-currency-select">Select base currency:</label>
    <select v-model="baseCurrency" id="base-currency-select">
      <option value="USD">USD</option>
      <option value="EUR">EUR</option>
      <option value="GBP">GBP</option>
      <option value="JPY">JPY</option>
      <option value="RUB">RUB</option>
    </select>
    <p v-for="(rate, key) in rates" :key="key">
      1 {{ baseCurrency }} = {{ rate }} {{ key }}
    </p>
  </div>
</template>

<script>
export default {
  props: {
    defaultBaseCurrency: {
      type: String,
      default: "USD",
    },
  },
  data() {
    return {
      baseCurrency: this.defaultBaseCurrency,
      rates: {},
    };
  },
  created() {
    this.fetchRates();
  },
  methods: {
    async fetchRates() {
      try {
        const res = await fetch(
          `https://openexchangerates.org/api/latest.json?app_id=f9c33c43337c4c038b8ae6c564f869ca&base=${this.baseCurrency}`
        );
        const data = await res.json();
        this.rates = data?.rates;
      } catch (error) {
        console.error(error);
      }
    },
  },
  watch: {
    baseCurrency: {
      handler: "fetchRates",
      immediate: true,
    },
  },
};
</script>
