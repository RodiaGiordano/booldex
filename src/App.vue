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
      const caught = this.captured.indexOf(data);

      if (this.captured[caught] != data) {
        this.captured.push(data);
        console.log(this.captured);
        console.log("sono diversi");
      } else {
        this.captured.splice(caught, 1);
        console.log(this.captured);
        console.log("sono uguali");
      }
    },
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
