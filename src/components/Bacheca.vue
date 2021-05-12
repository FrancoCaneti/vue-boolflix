<template>
  <main>
    <section>
      <h2>movie</h2>
      <div>
        <Copertina v-for="film in films" :key="film.id" />
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
  },
};
</script>

<style>
</style>