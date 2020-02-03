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
    </div>

    <div class="input-group mb-3">
      <div class="input-group-prepend">
        <label class="input-group-text" for="genero">Gênero</label>
      </div>
      <select v-model="selectedGenero" class="custom-select" required>
        <option v-for="(genero, index) in selectGenero" :key="index" :value="genero">{{ genero }} ></option>
      </select>
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
      }
    };
  },
  methods: {
    say: function(message) {
      alert(message);
    }
  },

  computed: {
    selGenero: function() {
      return this.selectGenero;
    }
  }
};
</script>

<style>
</style>