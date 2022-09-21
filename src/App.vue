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
        const url = `https://viacep.com.br/ws/${this.cep}/json/`;
        const res = await axios.get(url);
        this.endereco = res.data;
      },
    },
  };
</script>

<template>
  <div>
    <form @submit.prevent="buscar">
      <label for="busca"><h1>Procurador de CEP</h1></label><br>
      <input type="number" v-model="cep" class="busca" placeholder="99999999"><br>
      <button type="submit">Buscar</button>
    </form><br>
    <form class="end">
      <label for="rua">Rua:</label><br><input type="text" v-model="endereco.logradouro" /><br>
      <label for="bairro">Bairro:</label><br><input type="text" v-model="endereco.bairro" /><br>
      <label for="cidade">Cidade:</label><br><input type="text" v-model="endereco.localidade" /><br>
      <label for="num">Estado:</label><br><input type="text" v-model="endereco.uf"><br>
    </form>
  </div>
</template>

<style scoped>

  div{
    text-align: center;
    justify-content: center;
    margin-top: 11%;
    font-size: 20px;
  }

  input {
    width: 1000px;
    font-size: 24px;
    text-align: center;
  }

  button {
    width: 100px;
    font-size: 20px;
    border: solid grey 1px;
    border-radius: 7px;
    box-shadow: rgba(136, 165, 191, 0.48) 6px 2px 16px 0px, rgba(255, 255, 255, 0.8) -6px -2px 16px 0px;
    cursor: pointer;
    transition: 0.25s;
  }

  button:hover {
    transform: scale(1.1);
  }

  input {
    margin-bottom: 20px;
    border: 0;
    box-shadow: rgb(204, 219, 232) 3px 3px 6px 0px inset, rgba(255, 255, 255, 0.5) -3px -3px 6px 1px inset;
  }

</style>