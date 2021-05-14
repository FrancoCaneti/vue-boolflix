<template>
  <div class="cards">
    <img
      class="poster"
      v-if="details.poster_path"
      :src="`https://image.tmdb.org/t/p/w342${details.poster_path}`"
      alt=""
    />
    <img class="not" v-else src="../assets/notfound.jpg" alt="" />
    <div class="scheda">
      <ul>
        <li>{{ details.title ? details.title : details.name }}</li>
        <li>
          {{ details.original_title ? details.original_title : details.name }}
        </li>
        <li>
          {{ details.release_date ? details.release_date : details.name }}
        </li>
        <li>
          <img
            class="flags"
            v-if="flags(details.original_language)"
            :src="require(`@/assets/flags/${details.original_language}.png`)"
            :alt="details.original_language"
          />
          <span v-else>{{ details.original_language }}</span>
        </li>
        <li>
          {{ getStar(details.vote_average) }}
          <i
            v-for="i in getStar(details.vote_average)"
            :key="`piena-${i}`"
            class="fas fa-star"
          ></i>
          <i
            v-for="i in 5 - getStar(details.vote_average)"
            :key="`vuota-${i}`"
            class="far fa-star"
          ></i>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Copertina",
  props: {
    details: Object,
  },
  data() {
    return {
      bandiere: ["it", "en", "ja", "fr"],
    };
  },
  methods: {
    flags(lang) {
      return this.bandiere.includes(lang);
    },
    getStar(voto) {
      return Math.ceil(voto / 2);
    },
  },
};
</script>

<style scoped>
.flags {
  height: 12px;
}
.cards {
  margin: 10px;
  padding: 6px;
  border: 1px solid black;
  color: transparent;
  background-color: rgba(0, 128, 0, 0);
  padding: 0 10px;
  vertical-align: middle;
  text-align: center;
}

ul li {
  list-style: none;
  width: 340px;
  height: 102px;

  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
}

.not {
  border-radius: 10px;
  height: 440px;
  width: 335px;
}
.scheda {
  position: relative;
  bottom: 517px;
  height: 0px;
}
ul:hover {
  background-color: rgba(179, 5, 5, 0.801);
  color: white;
  text-transform: uppercase;
}
</style>