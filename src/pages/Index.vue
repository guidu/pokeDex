<template>
  <q-page class="flex flex-center">
    <div class="column items-center">
      <h2>{{name}}</h2>
        <q-img
            :src="url"
            width="250px"
          />
    </div>
    <div class="row justify-around full-width">
        <q-input standout v-model="search"/>
        <q-btn color="purple" label="Pesquisar" @click="getPokemon"/>
    </div>
  </q-page>
</template>

<script>

import api from '/src/services/api';
export default {
  
  name: "PageIndex",
  data() {
    return {
      name: '',
      url: '',
      search: 'charmander',
    }
  },
  async beforeMount() {
    await this.getPokemon() ;
  },
  methods: {
    getPokemon() {
   
        //criando uma requisição com AXIOS
      //(=>) Arrow function
      api.get('/pokemon/'+this.search+'/')
      .then((response) => { 
        console.log(response) 
        this.name = response.data.name;
        this.url = response.data.sprites.other.dream_world.front_default;
        this.triggerPositive ();
      })
      .catch((error) => 
        { 
          this.triggerNegative();
        }
      );
    },
     triggerPositive () {
        this.$q.notify({
          type: "positive",
          position: "top",
          message: "Pokemon encontrado."

        })
      },

      triggerNegative () {
        this.$q.notify({
          type: "negative",
          position: "top",
          message: "Pokemon não encontrado, verifique o nome correto."
        })
      }
  }
}
</script>
