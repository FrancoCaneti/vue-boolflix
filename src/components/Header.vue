<template>
  <div class="container">
    <img src="../assets/netflics.png" alt="" />
    <input type="text" id="" name="" v-model.trim="ricerca" />
    <button class="" @click.prevent="$emit('ricerca', risultati)"></button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Header",
  data() {
    return {
      ricerca: "",
      risultati: [],
    };
  },
  updated() {
    this.getApi();
    this.getApitv();
  },
  methods: {
    getApi() {
      axios
        .get("https://developers.themoviedb.org/3/search/movie", {
          params: {
            apikey: "9df4bf10e65cc42712e864ea9c9db428",
            query: this.ricerca,
          },
        })
        .then((res) => {
          this.risultati = res.data;
        });
    },
    getApitv() {
      axios
        .get("https://developers.themoviedb.org/3/search/tv", {
          params: {
            apikey: "9df4bf10e65cc42712e864ea9c9db428",
            query: this.ricerca,
          },
        })
        .then((res) => {
          this.risultati = res.data;
        });
    },
  },
};
</script>




<style>
.container {
  height: 100px;
  width: 100%;
  background-color: rgb(0, 0, 0);
  display: flex;
  align-items: center;
}
</style>