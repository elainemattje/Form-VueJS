<template>
  <div class="container">
    <h1>Bitcoin Prices</h1>
    <div class="bitcoin">
      <table class="painting">
        <thead>
          <th>Code</th>
          <th>Description</th>
          <th>Rate</th>
          <th>Symbol</th>
        </thead>
        <tbody>
          <transition-group name="fade" tag="tr" v-for="(bitcoin, index) in info" :key="index">
            <td :key="index + bitcoin.code">{{bitcoin.code}}</td>
            <td :key="index + bitcoin.description">{{bitcoin.description}}</td>
            <td :key="index + bitcoin.rate">{{bitcoin.rate}}</td>
            <td :key="index + bitcoin.symbol">{{bitcoin.symbol}}</td>
          </transition-group>
        </tbody>
      </table>
    </div>
    <transition name="fade">
      <div v-if="errored">Desculpe, não foi possível prosseguir com a sua solicitação.</div>
    </transition>
    <div v-if="loading">Loading...</div>
  </div>
</template>>
<script>
import axios from "axios";

export default {
  data() {
    return {
      info: null,
      loading: true,
      errored: false
    };
  },
  mounted: function() {
    setTimeout(() => {
      this.getBitcoinPrices();
    }, 5000);
  },
  methods: {
    getBitcoinPrices: function() {
      axios
        .get("https://api.coindesk.com/v1/bpi/currentprice.jsosn")
        .then(response => (this.info = response.data.bpi))
        .catch(error => {
          //eslint-disable-next-line no-console
          console.log(error);
          this.errored = true;
        })
        .finally(() => (this.loading = false));
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

.painting,
th,
td {
  border: solid black 1px;
  box-sizing: border-box;
  border-collapse: collapse;
  padding: 15px 15px;
  width: 800px;
  margin: 70px;
}

th,
td {
  width: 150px;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s, color 2s;
  color: pink;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
