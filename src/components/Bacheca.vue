<template>
  <main>
    <section v-show="films.length > 0" class="container-f">
      <h2>LISTA FILM</h2>
      <div class="film">
        <Copertina v-for="film in films" :key="film.id" :details="film" />
      </div>
    </section>
    <section v-show="series.length > 0" class="container-f">
      <h2>LISTA SERIE TV</h2>
      <div class="film">
        <Copertina v-for="serie in series" :key="serie.id" :details="serie" />
      </div>
    </section>
  </main>
</template>

<script>
import Copertina from "@/components/Copertina";

export default {
  name: "Bacheca",
  components: {
    Copertina,
  },
  props: {
    films: Array,
    series: Array,
  },
};
</script>

<style>
.container-f {
  background-color: #111;
  overflow-x: auto;
  height: 620px;
}

::-webkit-scrollbar {
  width: 0px;
  height: 5px;
  background: #111;
  margin-right: 10px;
}
::-webkit-scrollbar:hover {
  background-color: #111;
  border: none;
}
::-webkit-resizer {
  -webkit-border-radius: 4px;
  background-color: #ccc;
  border: none;
}
::-webkit-scrollbar-thumb {
  min-height: 5px;
  min-width: 0.8em;
  -webkit-border-radius: 10px;
  background-color: rgba(220, 20, 60, 0.753);
  border: none;
}
::-webkit-scrollbar-thumb:hover {
  background-color: rgb(248, 12, 60);
  border: none;
}
::-webkit-scrollbar-thumb:active {
  background-color: rgba(220, 20, 60, 0.753);
  border: none;
}
.film {
  display: flex;
  overflow-x: auto;
  flex-direction: row;
}

h2 {
  margin: 10px;
  color: #635f5f;
}
</style>