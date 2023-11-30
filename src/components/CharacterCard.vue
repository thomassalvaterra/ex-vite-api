<script>
export default {
  name: "CharacterCard",
  props: {
    info: Object
  }
}
</script>

<template>
  <div id="container">
    <h1 class="title">BEERS IN POLAND</h1>
    <h2 class="space">Nome Birrificio: {{ info.name }}</h2>
    <h2 class="space">Tipo di Birrificio: {{ info.brewery_type }}</h2>
    <h2 class="space">Indirizzo: {{ info.address_1 }}</h2>
    <h2 class="space">Città: {{ info.city }}</h2>
    <h2 class="space">Provincia: {{ info.state_province }}</h2>
    <h2 class="space">Codice Postale: {{ info.postal_code }}</h2>
    <h2 class="space">Paese: {{ info.country }}</h2>
    <!-- <input type="text" class="inpTxt">
    <button id="btn">Show Me!</button> -->
  </div>
</template>

<style scoped>
#container {
  width: 1400px;
  margin: 0 auto;
  min-height: 400px;
  border: 3px solid whitesmoke;
  display: flex;
  align-items: center;
  font-size: 13px;
}

.inpTxt {
  width: 300px;
  height: 30px;
  font-size: 20px;
}

#btn {
  margin-left: 20px;
  width: 70px;
}

.title {
  color: orange;
  text-align: center;
}

.space {
  text-align: center;
}
</style>

