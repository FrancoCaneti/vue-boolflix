<template>
  <div class="container">
    <img src="../assets/netflics.png" alt="" />
    <div class="list">Home</div>
    <div class="list">Serie Tv</div>
    <div class="list">Film</div>
    <div class="list">Nuovi e Popolari</div>
    <div class="list">La mia Lista</div>
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




<style scoped>
.container {
  height: 100px;
  width: 100%;
  background-color: rgb(2, 2, 2);
  display: flex;
  justify-content: flex-start;
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
  margin-left: 550px;
}
.top-bar {
  color: red;
}
.list {
  margin: 0 10px;
  color: #635f5f;
}
.list:hover {
  color: white;
  transform: scale(1.2);
}
</style>