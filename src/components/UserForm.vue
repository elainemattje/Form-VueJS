<template>
  <form class="form-group" id="register" name="novo_cadastro">
    <div class="input-group mb-3">
      <div class="input-group-prepend">
        <label class="input-group-text" for="nome">Nome</label>
      </div>
      <div>
        <input
          v-model="formulario.nome"
          placeholder="Digite o nome do candidato"
          class="form-control"
          type="text"
          required
        />
      </div>
      <br />
      <div class="input-group-prepend">
        <label class="input-group-text" for="telefone">Telefone</label>
      </div>
      <div>
        <input
          v-model="formulario.telefone"
          placeholder="Digite o telefone"
          class="form-control"
          type="text"
          required
        />
      </div>
      <br />
      <div class="input-group mb-3">
        <div class="input-group-prepend">
          <label class="input-group-text" for="genero">Gênero</label>
        </div>
        <label class="genero" for="f">Feminino</label>
        <input class="input" type="radio" id="f" value="Feminino" v-model="selectGenero" />
        <label class="genero" for="m">Masculino</label>
        <input class="input" type="radio" id="m" value="Masculino" v-model="selectGenero" />
      </div>
      <br />
      <div class="area">
        <div class="input-group mb-3">
          <div class="input-group-prepend">
            <label class="input-group-text" for="area">Área</label>
          </div>
          <select v-model="selectedArea" class="custom-select" required>
            <option v-for="(area, index) in selectArea" :key="index" :value="area">{{ area }}</option>
          </select>
        </div>
        <br />
        <div class="input-group mb-3">
          <div class="input-group-prepend">
            <label class="input-group-text" for="experiencia">Experiência</label>
          </div>
          <select v-model="selectedExperiencia" class="custom-select" required>
            <option
              v-for="(experiencia, index) in selectExperiencia"
              :key="index"
              :value="experiencia"
            >{{ experiencia }}</option>
          </select>
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
        />
      </div>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      formulario: {
        nome: "",
        telefone: ""
      },
      selectedGenero: "",
      selectGenero: {
        feminino: "feminino",
        masculino: "masculino"
      },
      selectedArea: "",
      selectArea: {
        frontend: "FrontEnd",
        backend: "BackEnd",
        designer: "Designer",
        qa: "QA",
        content: "Content"
      },
      selectedExperiencia: "",
      selectExperiencia: {
        ate_6_meses: "Até 6 meses",
        de_6_meses_a_1_ano: "De 6 meses a 1 ano",
        ano_1: "1 Ano",
        ano_2: "2 Anos",
        acima_de_2_anos: "Acima de 2 anos"
      }
    };
  },
  methods: {
    say: function(message) {
      alert(message);
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}
.form-group {
  width: 30%;
  height: 50%;
  background-color: rgb(193, 195, 202);
  padding: 10px;
}
.input-group-prepend {
  font-size: 20px;
}
.form-control {
  width: 100%;
  height: 30px;
  margin: 5px 20px 0 0;
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
}
</style>