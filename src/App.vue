<script>
import CharacterCard from "./components/CharacterCard.vue"; //importo componente figlio

import axios from 'axios'; //importo Axios
import { store } from "./store.js" //state management

export default {
  components: {
    CharacterCard
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
      axios.get(this.store.apiUrl).then(risultato => {
        this.store.birre = risultato.data;
        console.log(risultato.data);
      });
    },
  }
}
</script>

<template>
  <main>
    <CharacterCard v-for="birra in store.birre" :info="birra" />
  </main>
</template>

<style scoped></style>
