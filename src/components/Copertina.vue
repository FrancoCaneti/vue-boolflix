<template>
  <div class="cards">
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
      <li>{{ details.vote_average }}</li>
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
      bandiere: ["it", "en"],
    };
  },
  methods: {
    flags(lang) {
      return this.bandiere.includes(lang);
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
</style>