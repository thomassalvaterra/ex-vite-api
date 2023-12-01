<script>
import { store } from "../store.js" //state management

export default {
    name: "AppSearch",
    data() {
        return {
            store
        }
    },
    methods: {
        search() {
            console.log("Cerca: ", this.store.searchString);
            this.$emit("search");
        }
    },
    mounted() {

    }
}
</script>

<template>
    <div class="container">
        <input class="inpTxt" placeholder="Cerca..." v-model="store.searchString" @keyup.enter="$emit('search')">
        <button id="btn" @click="search">Cerca</button>
    </div>
</template>

<style scoped>
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}

.inpTxt {
    width: 300px;
    height: 30px;
    font-size: 20px;
    margin: 30px;
}

#btn {
    margin-left: 20px;
    width: 90px;
    height: 30px;
    background-color: orange;
    color: white;
}
</style>