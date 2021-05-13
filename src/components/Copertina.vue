<template>
  <div class="cards">
    <img
      v-if="details.poster_path"
      :src="`https://image.tmdb.org/t/p/w185${details.poster_path}`"
      alt=""
    />
    <img class="not" v-else src="../assets/notfound.jpg" alt="" />
    <div>
      <ul>
        <li>{{ details.title ? details.title : details.name }}</li>
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
  padding: 10px;
  width: 150px;
  background-color: #ffffff;
}
ul {
  border: 1px solid black;
}
.not {
  height: 50px;
  width: 100px;
}
</style>