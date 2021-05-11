<template>
  <div class="container">
    <img src="../assets/netflics.png" alt="" />
    <input
      type="text"
      id=""
      palceholder="Cosa vuoi guardare..."
      name=""
      v-model.trim="ricercaTesto"
    />
    <button class="btn" @click="$emit('ricerca testo', ricercaTesto)">✓</button>
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
  align-items: center;
}
.btn {
  padding: 8px;
}
</style>