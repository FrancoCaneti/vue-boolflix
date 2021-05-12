<template>
  <div id="app">
    <!--Header-->
    <header>
      <Header @ricerca="getSearch" />
    </header>
    <!--Main-->
    <main>
      <Bacheca :films="listaFilm" />
    </main>
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
import Bacheca from "@/components/Bacheca.vue";
export default {
  name: "App",
  components: {
    Header,
    Bacheca,
  },
  data() {
    return {
      apiURL: "https://api.themoviedb.org/3/search/",
      apiKey: "9df4bf10e65cc42712e864ea9c9db428",
      listaFilm: [],
      listaSerie: [],
    };
  },
  methods: {
    getSearch(ricerca) {
      console.log(ricerca);
      if (ricerca !== "") {
        axios
          .get(this.apiURL + "movie", {
            params: {
              api_key: this.apiKey,
              query: ricerca,
              lenguage: "it-IT",
            },
          })
          .then((res) => {
            this.listaFilm = res.data.results;
          });
      }
    },
  },
};
</script>




<style >
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
