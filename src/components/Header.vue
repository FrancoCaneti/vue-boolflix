<template>
  <div class="container">
    <img src="../assets/netflics.png" alt="" />
    <div>
      <input
        class="search"
        type="text"
        placeholder="Cosa vuoi guardare?"
        v-model.trim="ricercaTesto"
      />

      <button class="btn" @click="$emit('ricerca', ricercaTesto)">
        <i class="fas fa-search">Q</i>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      ricercaTesto: "",
    };
  },
};
</script>




<style>
.container {
  height: 100px;
  width: 100%;
  background-color: #000;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.btn {
  margin-right: 20px;
  background-color: transparent;
  color: white;
}
.search {
  border-radius: 5%;
  background: transparent;
  border-radius: 5%;
  padding: 2px;
  color: white;
}
</style>