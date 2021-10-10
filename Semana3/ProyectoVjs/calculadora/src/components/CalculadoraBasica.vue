<template>
  <v-container>
    <titulo />
    <v-row>
      <v-col class="text-center">
        <h1>Calculadora Básica</h1>
      </v-col>
    </v-row>

    <hr />
    <v-row>
      <v-col>
        <v-text-field
          type="number"
          label="Numero 1"
          :rules="rules"
          hide-details="auto"
          v-model="n1"
        ></v-text-field>
      </v-col>
      <v-col>
        <v-text-field
          type="number"
          label="Numero 2"
          :rules="rules"
          hide-details="auto"
          v-model="n2"
        ></v-text-field>
      </v-col>
    </v-row>

    <v-row class="text-center">
      <v-col
        ><v-btn color="primary" elevation="9" outlined rounded @click="sumar()"
          >Sumar</v-btn
        ></v-col
      >
      <v-col
        ><v-btn color="primary" elevation="9" outlined rounded @click="restar()"
          >Restar</v-btn
        ></v-col
      >

      <v-col
        ><v-btn
          color="primary"
          elevation="9"
          outlined
          rounded
          @click="multiplicar()"
          >Multiplicar</v-btn
        ></v-col
      >
      <v-col
        ><v-btn
          color="primary"
          elevation="9"
          outlined
          rounded
          @click="dividir()"
          >Dividir</v-btn
        ></v-col
      >
    </v-row>

    <br />
    {{ resp }}
  </v-container>
</template>

<script>
import Titulo from "./Titulo.vue";
export default {
  name: "CalculadoraBasica",
  components: { Titulo },
  data: () => {
    return {
      n1: null,
      n2: null,
      resp: "",
      rules: [
        (value) => !!value || "Requerido.",
        (value) => (value && value.length >= 2) || "Min 2 Caracteres",
      ],
    };
  },
  methods: {
    sumar() {
      this.resp = parseFloat(this.n1) + parseFloat(this.n2);
    },
    restar() {
      this.resp = parseFloat(this.n1) - parseFloat(this.n2);
    },
    multiplicar() {
      this.resp = parseFloat(this.n1) * parseFloat(this.n2);
    },
    dividir() {
      if (this.n2 == 0) {
        alert("Not a number");
      } else {
        this.resp = parseFloat(this.n1) / parseFloat(this.n2);
      }
    },
  },
};
</script>

<style></style>
