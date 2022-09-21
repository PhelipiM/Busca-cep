<script>
  import axios from "axios";
  export default {
    data() {   
      return{
        cep:"",
        endereco:{},
      };
    },
  methods:{
    async buscar(){
      const url=`https://viacep.com.br/ws/${this.cep}/json`;
      const res = await axios.get(url);
      this.endereco=res.data;
    },
  },
};


</script>
<template>
  <H1>Buscar cep</H1>
  <form @submit.prevent="buscar">
    <input type="text" v-model="cep" placeholder="Digite o cep"/>
    <button type="submit">Buscar</button>
  </form>
  <form class="end">
    <label for="rua">Rua</label>
    <input type="text" v-model="endereco.logradouro"/>
    <label for="num">numero</label>
    <input type="text" v-model="endereco.numero"/>
    <label for="bairro">bairro</label>
    <input type="text" v-model="endereco.bairro"/>
  </form>
</template>
<style scoped>
.end{
  display: flex;
  flex-direction:column ;
}

</style>