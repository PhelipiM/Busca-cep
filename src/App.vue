<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      endereco: {},
    };
  },
  methods: {
    async buscar() {
      const url = `https://viacep.com.br/ws/${this.cep}/json`;
      const res = await axios.get(url);
      this.endereco = res.data;
    },
  },
};
</script>
<template>
  <div class="corpo">
    <H1>Buscar cep</H1>
    <form class="contexto" @submit.prevent="buscar">
      <input type="text" v-model="cep" placeholder="Digite o cep" />
      <button type="submit">Buscar</button>
    </form>
    <form class="end">
      <label for="rua">Rua</label>
      <input type="text" v-model="endereco.logradouro" />
      <label for="num">numero</label>
      <input type="text" v-model="endereco.numero" />
      <label for="bairro">bairro</label>
      <input type="text" v-model="endereco.bairro" />
    </form>
  </div>
</template>
<style scoped>
.end {
  display: flex;
  flex-direction: column;
}
H1 {
  display: flex;
  align-items: center;
}
#app {
  width: 100%;
  height: 100%;
  font-family: "Open Sans", sans-serif;
  background-color: #092756;
  align-items: center;
}
.corpo {
  border: solid;
  border-radius: 50px;
  position: absolute;
  justify-content: center;
  top: 50%;
  left: 50%;
  margin: -150px 0 0 -250px;
  width: 450px;
  height: 350px;
  padding: 20px;
  font-family: "Open Sans", sans-serif;
}

h1 {
  font-family: "Open Sans", sans-serif;
  color: rgb(5, 1, 1);
  text-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
  letter-spacing: 1px;
  text-align: center;
}

input {
  width: 70%;
  margin-bottom: 10px;
  background: rgb(233, 232, 232);
  border: none;
  outline: none;
  padding: 10px;
  font-size: 16px;
  color: #213b65;
  border-radius: 6px;
  transition: 0.5s;
  font-family: "Open Sans", sans-serif;
}

input:focus {
  background-color: #9a9b9b;
}
button {
  margin: 10px;
  font-family: "Open Sans", sans-serif;
  color: #064716;
  font-size: 16px;
  background-color: #199738;
}
</style>
