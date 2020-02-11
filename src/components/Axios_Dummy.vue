<template>
  <div class="container">
    <h1>Personal Data</h1>
    <div class="bitcoin">
      <table class="painting">
        <thead>
          <th>ID</th>
          <th>Name</th>
          <th>Age</th>
          <th>Salary</th>
        </thead>
        <tbody>
          <transition-group name="fade" tag="tr" v-for="(inform, index) in info" :key="index">
            <td :key="`${index}_id`">{{inform.id}}</td>
            <td :key="`${index}_name`">{{inform.employee_name}}</td>
            <td :key="`${index}_age`">{{inform.employee_age}}</td>
            <td :key="`${index}_salary`">{{inform.employee_salary}}</td>
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
  name: "AxiosDummy",
  data() {
    return {
      info: [],
      loading: true,
      errored: false
    };
  },
  mounted: function() {
    setTimeout(() => {
      this.getPersonalData();
    }, 2000);
  },

  methods: {
    getPersonalData: function() {
      axios
        .get("http://dummy.restapiexample.com/api/v1/employees")
        .then(response => {
          this.info = response.data.data;
        });
      // .catch(error => {
      //   //eslint-disable-next-line no-console
      //   console.log(error);
      //   this.errored = true;
      // });
      // .finally(() => (this.loading = false));
    }
  }
};
</script>>
<style>
.container {
  width: 100%;
  height: 100%;
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
