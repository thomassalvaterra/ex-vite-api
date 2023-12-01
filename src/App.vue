<script>
import CharacterCard from "./components/CharacterCard.vue"; //importo componente figlio
import AppSearch from "./components/AppSearch.vue"; //importo componente figlio

import axios from 'axios'; //importo Axios
import { store } from "./store.js" //state management

export default {
  components: {
    CharacterCard,
    AppSearch
  },
  data() {
    return {
      store,
    }
  },
  mounted() {
    this.getProva();
  },
  methods: {
    getProva() {
      let indirizzo = this.store.apiUrl;


      if (this.store.searchString.length) {
        // indirizzo += `?by_type=`;

        axios.get(indirizzo).then(risultato => {
          this.store.birre = risultato.data;
          console.log(risultato.data);
        })

      } else {
        axios.get("https://api.openbrewerydb.org/v1/breweries?by_country=poland&per_page=10&by_type=" + store.searchString).then(result => {
          this.store.birre = result.data;
          console.log(result.data);
        }).catch(error => {
          this.store.birre = [];
          console.error("Errore");
        });
      }


      console.log("Richiama: ", indirizzo);




    },
  }
}
</script>

<template>
  <header>
    <AppSearch @search="getProva" />
  </header>
  <main>
    <CharacterCard v-for="birra in store.birre" :info="birra" />
    <p class="center" v-if="store.searchString.length == 0">Nessun risultato</p>
  </main>
</template>

<style scoped>
.center {
  text-align: center;
  font-size: 20px;
}
</style>
