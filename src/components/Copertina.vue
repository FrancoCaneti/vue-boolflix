<template>
  <div class="locandina">
    <img
      class="poster"
      v-if="details.poster_path"
      :src="`https://image.tmdb.org/t/p/w342${details.poster_path}`"
      alt=""
    />
    <img class="not poster" v-else src="../assets/notfound.jpg" alt="" />

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
          class="fas fa-star piena"
        ></i>
        <i
          v-for="i in 5 - getStar(details.vote_average)"
          :key="`vuota-${i}`"
          class="far fa-star vuota"
        ></i>
      </li>
    </ul>
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

<style>
.flags {
  height: 10px;
}

.locandina {
  margin: 0 10px;
  height: 540px;
}

ul li {
  list-style: none;
  margin: 0 10px;
  width: 300px;
  height: 102px;
}
ul {
  position: relative;
  top: -518px;
  padding: 3px;
  background-color: transparent;
  color: transparent;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}

ul:hover {
  background-color: rgba(63, 57, 57, 0.76);
  color: rgb(255, 255, 255);
}

.not {
  border-radius: 10px;
  height: 440px;
  width: 335px;
}
</style>