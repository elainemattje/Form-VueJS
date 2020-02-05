<template>
  <h1>Consulta CEP</h1>
  <!-- <div class="consultaCEP"> -->
  <!-- <input v-model="consultaCEP.cep" placeholder="Digite o cep" type="text" {{ cep }} /> -->
  <!-- </div> -->
</template>>
<script>
// import axios from "axios";
export default {
  data() {
    return {
      consultaCEP: {
        cep: null
      }
    };
  },
  created: function() {
    this.buscaCep();
  },
  methods: {
    buscaCep: function() {
      //   axios.get("http://").then(response => (this.cep = response));
    }
  }
};
</script>>
