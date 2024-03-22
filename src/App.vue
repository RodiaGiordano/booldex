<script>
import LeftPoke from "./components/LeftPoke.vue";
import RightPoke from "./components/RightPoke.vue";

export default {
  data() {
    return {
      captured: [],
    };
  },

  components: {
    LeftPoke,
    RightPoke,
  },

  methods: {
    saveToggle(data) {
      const pokedex = JSON.parse(localStorage.getItem("pokedex")) || [];
      const captured = pokedex.findIndex((item) => item.name === data.name);
      if (captured != -1) {
        this.captured.splice(captured, 1);
        pokedex.splice(captured, 1);
        localStorage.setItem(`pokedex`, JSON.stringify(pokedex));
      } else {
        pokedex.push(data);
        this.captured.push(data.name);
        localStorage.setItem(`pokedex`, JSON.stringify(pokedex));
      }
    },
  },

  mounted() {
    const pokedex = JSON.parse(localStorage.getItem("pokedex")) || [];
    pokedex.forEach((pokemon) => this.captured.push(pokemon.name));
  },
};
</script>

<template>
  <div class="container">
    <div class="booldex">
      <LeftPoke @saveToggle="saveToggle" :captured="captured" />

      <RightPoke :captured="captured" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use "./assets/variables.scss" as *;

.container {
  display: flex;
  justify-content: center;
  align-items: center;

  min-width: 1200px;
  padding: 50px;

  .booldex {
    background-color: $bg-primary;
    border: 10px solid $bd-primary;
    border-radius: 40px;
    height: 800px;
    width: 1100px;
    display: flex;
    > * {
      flex: 1;
    }
  }
}
</style>
