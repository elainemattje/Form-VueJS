<template>
  <div class="container">
    <h1>Bitcoin Prices</h1>
    {{currency.description}}
  </div>
</template>>
<script>
import axios from "axios";

export default {
  data() {
    return {
      currency: {
        description: null
      }
    };
  },
  created: function() {
    this.bitcoinPrices();
  },
  methods: {
    bitcoinPrices: function() {
      axios
        .get("https://api.coindesk.com/v1/bpi/currentprice.json")
        .then(response => (this.currency.description = response.data.bpi));
    }
  }
};
</script>>
<style>
.container {
  width: 50%;
  height: 500px;
  background-color: rgb(122, 212, 235);
  text-align: center;
  padding: 10px;
}
</style>
