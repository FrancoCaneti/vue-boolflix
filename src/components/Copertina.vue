<template>
  <div class="cards">
    <img
      class="poster"
      v-if="details.poster_path"
      :src="`https://image.tmdb.org/t/p/w342${details.poster_path}`"
      alt=""
    />
    <img class="not poster" v-else src="../assets/notfound.jpg" alt="" />
    <div class="">
      <ul>
        <li>
          {{ details.title ? details.title : details.name }}
        </li>
        <li>
          {{ details.original_title ? details.original_title : details.name }}
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
      bandiere: ["it", "en"],
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

<style>
.flags {
  height: 10px;
}
.cards {
  margin: 10px;
  padding: 6px;
  border: 1px solid black;
}
ul li {
  list-style: none;
  display: inline-block;

  width: 150px;
  height: 60px;
  background-color: rgb(248, 248, 248);
}
ul {
  border: 1px solid black;
}
.not {
  height: 220px;
  width: 180px;
}
</style>