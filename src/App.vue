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
  <div class="container text-center">
    <form @submit.prevent="buscar">
      <p class="text-uppercase fs-1 fst-italic">Procurador de CEP</p>
      <input type="number" v-model="cep" class="busca col-2 text-center form-control" placeholder="99999999"><br>
      <button type="submit" class="btn btn-success col-1">Buscar</button>
    </form>
    <div class="container col-6">
      <ul class="list-group list-group-horizontal">
        <li class="list-group-item">CEP</li>
        <input class="list-group-item" type="text" v-model="endereco.cep">
      </ul>
      <ul class="list-group list-group-horizontal-sm">
        <li class="list-group-item">Rua</li>
        <input class="list-group-item" type="text" v-model="endereco.logradouro">
      </ul>
      <ul class="list-group list-group-horizontal-md">
        <li class="list-group-item">Bairro</li>
        <input class="list-group-item" type="text" v-model="endereco.bairro">
      </ul>
      <ul class="list-group list-group-horizontal-lg">
        <li class="list-group-item">Cidade</li>
        <input class="list-group-item" type="text" v-model="endereco.localidade">
      </ul>
      <ul class="list-group list-group-horizontal-xl">
        <li class="list-group-item">Estado</li>
        <input class="list-group-item" type="text" v-model="endereco.uf">
      </ul>
    </div>
    <img src="https://c.tenor.com/cCADMf95jDsAAAAM/alien-dance.gif" class="img-fluid" />
    <img src="https://c.tenor.com/cCADMf95jDsAAAAM/alien-dance.gif" class="img-fluid" />
    <img src="https://c.tenor.com/cCADMf95jDsAAAAM/alien-dance.gif" class="img-fluid" />
    <img src="https://c.tenor.com/cCADMf95jDsAAAAM/alien-dance.gif" class="img-fluid" />
    <img src="https://c.tenor.com/cCADMf95jDsAAAAM/alien-dance.gif" class="img-fluid" />
  </div>
</template>

<style scoped>

  .container{
    justify-content: center;
    margin-top: 5%;
    font-size: 20px;
  }

  form button {
    margin-top: 10px;
  }

  .list-group-item {
    text-align: center;
    width: 100%;
  }

  ul li {
    background-color: rgb(233, 233, 233);
  }

</style>