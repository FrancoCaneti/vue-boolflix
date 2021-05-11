<template>
  <div id="app">
    <!--Header-->
    <header>
      <Header @searchingText="updateSearch" />
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
      listaFilm: [],
      listaSerieTv: [],
      apiUrlfilm: "https://api.themoviedb.org/3/search/movie",
      apiUrltv: "https://api.themoviedb.org/3/search/tv",
    };
  },
  methods: {
    updateSearch(text) {
      if (text.length > 0) {
        axios
          .get(this.apiUrlfilm, {
            params: {
              api_key: "9df4bf10e65cc42712e864ea9c9db428",
              query: text,
            },
          })
          .then((res) => {
            this.movieList = res.data.results;
            console.log(this.listaFilm);
          })
          .catch((err) => {
            console.log("Error", err);
          });
      } else {
        alert("Inserisci una lettere per iniziare la ricerca");
      }
      if (text.length > 0) {
        axios
          .get(this.apiUrltv, {
            params: {
              api_key: "9df4bf10e65cc42712e864ea9c9db428",
              query: text,
            },
          })
          .then((result) => {
            this.seriesList = result.data.results;
            console.log(this.movieList);
          })
          .catch((error) => {
            console.log("Error", error);
          });
      } else {
        alert("Inserisci una lettere per iniziare la ricerca");
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
