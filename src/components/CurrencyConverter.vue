<template>
  <div>
    <input type="text" placeholder="Format:15 USD in RUB" v-model="input" />
    <button @click="convertCurrency">Convert</button>
    <p>{{ output }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input: "",
      output: "",
      rate: 0,
    };
  },
  methods: {
    convertCurrency() {
      try {
        fetch(
          "https://openexchangerates.org/api/latest.json?app_id=f9c33c43337c4c038b8ae6c564f869ca"
        )
          .then((res) => res.json())
          .then((data) => {
            const [value, from, in_, to] = this.input.split(" ");
            this.rate = data.rates[to] / data.rates[from];
            this.output = value * this.rate;
          });
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>
