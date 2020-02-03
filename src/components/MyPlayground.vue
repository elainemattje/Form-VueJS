<template>
  <div>
    <!-- Uso de computed property + props -->
    <h1>{{propsWithMoreText}}</h1>Array
    <!-- V-for com keys -->
    <h1 v-for="(fruit, index) in arrayFruits" :key="index">{{ fruit }} {{index}}</h1>
    <div class="input-group mb-3">
      <div class="input-group-prepend">
        <label class="input-group-text" for="genero">Gênero</label>
      </div>
      <select v-model="selectFruits" class="custom-select" required>
        <option
          v-for="(fruit, index) in arrayFruits"
          :key="index"
        >{{ fruit }} {{index}}selected value="banana"></option>
        <option
          v-for="(fruit, index) in arrayFruits"
          :key="index"
        >{{ fruit }} {{index}}selected value="maca"></option>
        <option
          v-for="(fruit, index) in arrayFruits"
          :key="index"
        >{{ fruit }} {{index}}selected value="laranja"></option>
      </select>
    </div>
    <!-- <h1>{{ fruitsConcatArrayFruits }}</h1> -->
    <br />

    <p>Object</p>
    <h1 v-for="(fruit, index) in objectFruits" :key="index">{{ fruit }} {{index}}</h1>
    <h1>{{ fruitsConcatObjectFruits }}</h1>

    <br />
    <p>Array de objects</p>
    <h1 v-for="(fruit, index) in arrayObjectFruits" :key="index">{{ fruit.nome }} {{index}}</h1>
    <h1>{{ fruitsConcatArrayObjectFruits }}</h1>
  </div>
</template>

<script>
export default {
  name: "MyPlayground",
  props: {
    msg: {
      type: String,
      default: "Texto default"
    }
  },
  data() {
    return {
      selectFruits: "banana",
      allFruitsObjectFruits: "",
      arrayFruits: ["Banana", "Maçã", "Laranja"], // array (igual a lista de objetos e diferente do array de objetos)
      objectFruits: {
        // lista de objetos
        0: "Abacaxi",
        1: "Mamão",
        2: "Pera"
      },
      arrayObjectFruits: [
        // array de objetos
        {
          nome: "Caqui"
        },
        {
          nome: "Abacate"
        },
        {
          nome: "Limao"
        }
      ]
    };
  },
  computed: {
    propsWithMoreText: function() {
      return this.msg + "MAIS TEXTOOOO";
    },

    fruitsConcatArrayFruits: function() {
      //   return this.arrayFrutas[0] + this.arrayFrutas[1];

      let allFruits = "";

      this.arrayFruits.forEach(fruit => {
        allFruits += fruit;
      });

      return allFruits;
    },

    fruitsConcatObjectFruits: function() {
      //   return this.arrayFrutas[0] + this.arrayFrutas[1];
      let concat = "";

      for (var fruit in this.objectFruits) {
        concat += this.objectFruits[fruit];
      }
      // this.objectFruits.forEach(index => {
      //   concat += index;
      // });

      return concat;
    },

    fruitsConcatArrayObjectFruits: function() {
      //   return this.arrayFrutas[0] + this.arrayFrutas[1];
      let concat2 = "";

      // this.arrayObjectFruits.forEach(fruit => {
      //   concat2 += this.arrayObjectFruits[fruit];
      // });

      for (var fruit in this.arrayObjectFruits) {
        concat2 += this.arrayObjectFruits[fruit];
      }
      // this.objectFruits.forEach(index => {
      //   concat += index;
      // });

      return concat2;
    }
  },
  mounted() {
    let that = this;

    setTimeout(() => {
      that.arrayFruits = ["Uva", "Manga"];
    }, 3000);
  }
};
// mounted() {
//   let that = this;

//   setTimeout(() => {
//     that.arrayFruits = ["Uva", "Manga"];
//   }, 3000);
// }
</script>

<style>
</style>