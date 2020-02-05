<template>
  <form class="form-group" id="register" name="novo_cadastro">
    <div class="input-group-prepend">
      <label class="input-group-text" for="name">Nome</label>
    </div>
    <div>
      <input
        v-model="formulario.name"
        placeholder="Digite o nome do candidato"
        class="form-control"
        type="text"
        required
      />
    </div>
    <br />
    <div class="input-group-prepend">
      <label class="input-group-text" for="phone">Telefone</label>
    </div>
    <div>
      <input
        v-model="formulario.phone"
        placeholder="Digite o telefone"
        class="form-control"
        type="text"
        required
      />
    </div>
    <br />
    <div class="input-group mb-3">
      <div class="input-group-prepend">
        <label class="input-group-text" for="gender">Gênero</label>
      </div>
      <label class="genero" for="f">Feminino</label>
      <input class="input" type="radio" id="f" value="Feminino" v-model="formulario.selectedgender" />
      <label class="genero" for="m">Masculino</label>
      <input
        class="input"
        type="radio"
        id="m"
        value="Masculino"
        v-model="formulario.selectedgender"
      />
    </div>
    <br />
    <div class="area">
      <div class="input-group mb-3">
        <div class="input-group-prepend">
          <label class="input-group-text" for="area">Área</label>
        </div>
        <select v-model="formulario.selectedArea" class="custom-select" required>
          <option v-for="(area, index) in selectArea" :key="index" :value="area">{{ area }}</option>
        </select>
      </div>
      <br />
      <div class="input-group mb-3">
        <div class="input-group-prepend">
          <label class="input-group-text" for="experience">Experiência</label>
        </div>
        <select v-model="formulario.selectedExperience" class="custom-select" required>
          <option
            v-for="(experience, index) in selectExperience"
            :key="index"
            :value="experience"
          >{{ experience }}</option>
        </select>
      </div>
      <br />
      <div class="input-group-prepend">
        <label class="input-group-text" for="considerations">Observações</label>
      </div>
      <div>
        <textarea
          v-model="formulario.considerations"
          placeholder="Observações"
          class="form-control--textarea"
          type="text"
        />
      </div>
    </div>
    <br />
    <div>
      <input
        class="btn btn-primary"
        type="submit"
        name="submit"
        value="Cadastrar"
        @click="say('Candidadto cadastrado')"
        :disabled="!isValid"
      />
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      formulario: {
        name: "",
        phone: "",
        selectedgender: "",
        selectedArea: "",
        selectedExperience: "",
        considerations: " "
      },
      selectgender: {
        feminino: "feminino",
        masculino: "masculino"
      },
      selectArea: {
        frontend: "FrontEnd",
        backend: "BackEnd",
        designer: "Designer",
        qa: "QA",
        content: "Content"
      },
      selectExperience: {
        upTo6Months: "Até 6 meses",
        from6MonthsTo1Year: "De 6 meses a 1 ano",
        Year1: "1 Ano",
        Year2: "2 Anos",
        moreThan2Years: "Acima de 2 anos"
      }
    };
  },
  methods: {
    say: function(message) {
      alert(message);
    }
  },
  computed: {
    isValid: function() {
      return this.formulario.nome !== "" && this.formulario.telefone !== "";
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}
.form-group {
  width: 40%;
  height: 50%;
  background-color: rgb(193, 195, 202);
  padding: 10px;
  border-radius: 5px;
}
.input-group-prepend {
  font-size: 20px;
}
.form-control {
  width: 100%;
  height: 30px;
  margin: 5px 20px 0 0;
  font-size: 15px;
}
.form-control--textarea {
  width: 100%;
  height: 100px;
}
.custom-select {
  width: 100%;
  height: 30px;
  margin: 5px 20px 0 0;
}
.area {
  display: block;
}
.genero {
  margin: 5px 10px 0 0;
}
.input {
  margin: 5px 25px 0 0;
}
.btn {
  width: 30%;
  padding: 10px;
  background-color: rgb(73, 76, 77);
  color: white;
  font-size: 18px;
}
</style>