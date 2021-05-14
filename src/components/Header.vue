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
    <div>
      <i class="fas fa-gift icon icons"></i>
    </div>
    <div>
      <i class="fas fa-bell icon icons"></i>
    </div>
    <div>
      <img class="panda" src="../assets/panda.jpg" alt="" />
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
  margin-left: 450px;
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
.panda {
  height: 50px;
  margin-right: 10px;
  margin-left: 10px;
}
.icon {
  color: #635f5f;
  margin: 0 10px;
}
.icons:hover {
  transform: scale(2);
  color: white;
}
</style>