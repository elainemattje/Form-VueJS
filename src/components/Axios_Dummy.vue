<template>
  <div class="container">
    <h1>Personal Data</h1>
    <div class="employees">
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
    <div class="register">
      <div class="register--item">
        <input
          class="input"
          type="text"
          name="name"
          v-model="inform.employee_name"
          placeholder="Name"
        />
      </div>
      <div class="register--item">
        <input
          class="input"
          type="number"
          min="16"
          max="110"
          name="age"
          v-model="inform.employee_age"
          placeholder="Age"
        />
      </div>
      <div class="register--item">
        <input
          class="input"
          type="number"
          name="salary"
          v-model="inform.employee_salary"
          placeholder="Salary"
        />
      </div>
      <div class="register--item">
        <button @click="register" class="btn" type="submit">Register</button>
      </div>
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
      inform: {
        id: "",
        employee_name: "",
        employee_age: "",
        employee_salary: ""
      },
      info: [],
      loading: true,
      errored: false
    };
  },
  mounted() {
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
        })
        .catch(error => {
          //eslint-disable-next-line no-console
          console.log(error);
          this.errored = true;
        })
        .finally(() => (this.loading = false));
    },
    register: function() {
      axios
        .post("http://dummy.restapiexample.com/api/v1/create", {
          name: `${this.inform.employee_name}`,
          age: `${this.inform.employee_age}`,
          salary: `${this.inform.employee_salary}`
        })
        .then(response => {
          //eslint-disable-next-line no-console
          console.log(response);
        });
    }
  }
};
</script>>
<style>
h1 {
  margin: 10px;
  width: 800px;
  text-align: center;
}

.painting,
th,
td {
  border: solid black 1px;
  box-sizing: border-box;
  border-collapse: collapse;
  padding: 10px 10px;
  width: 800px;
  margin: 20px;
  background-color: rgb(104, 196, 233);
  text-align: center;
}

th {
  background-color: rgb(73, 185, 230);
}
th,
td {
  width: 150px;
}

.register {
  display: block;
}

.register--item {
  text-align: left;
}

.name {
  font-size: 20px;
  margin: 10px 10px 10px 20px;
}

.input {
  margin: 10px 0 0 20px;
  padding: 5px;
  width: 780px;
  height: 20px;
}

.btn {
  font-size: 15px;
  padding: 8px;
  width: 100px;
  margin: 10px 0 0 20px;
  background-color: rgb(73, 185, 230);
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
