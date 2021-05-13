<template>
  <div class="container">
    <img src="../assets/netflics.png" alt="" />
    <div></div>
    <div>
      <input
        class="search"
        type="text"
        placeholder="Cosa vuoi guardare?"
        v-model.trim="ricercaTesto"
      />

      <button class="btn" @click="$emit('ricerca', ricercaTesto)">
        <i class="fas fa-search"></i>
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
  background-color: rgb(0, 0, 0);
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
.top-bar {
  color: red;
}
</style>