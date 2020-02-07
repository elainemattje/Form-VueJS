<template>
  <div class="container">
    <h1>Consulta Bitcoin</h1>
    {{consulta.bitcoin}}
  </div>
</template>>
<script>
import axios from "axios";

export default {
  data() {
    return {
      consulta: {
        bitcoin: null
      }
    };
  },
  created: function() {
    this.buscaBitcoin();
  },
  methods: {
    buscaBitcoin: function() {
      axios
        .get("https://api.coindesk.com/v1/bpi/currentprice.json")
        .then(response => (this.consulta.bitcoin = response));
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
