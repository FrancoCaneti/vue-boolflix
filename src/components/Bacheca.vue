<template>
  <main>
    <div v-for="film in films" :key="film.id"></div>
  </main>
</template>

<script>
export default {
  name: "Bacheca",

  props: ["films"],
};
</script>

<style>
</style>