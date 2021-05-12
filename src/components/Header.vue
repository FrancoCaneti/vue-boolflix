<template>
  <div class="container">
    <img src="../assets/netflics.png" alt="" />
    <div>
      <input
        type="text"
        placeholder="Cosa vuoi guardare?"
        v-model.trim="ricercaTesto"
      />

      <button @click="$emit('ricerca', ricercaTesto)">Cerca</button>
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
  margin-right: 10px;
}
</style>