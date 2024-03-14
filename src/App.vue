<script>
import LeftPoke from "./components/LeftPoke.vue";
import RightPoke from "./components/RightPoke.vue";

export default {
  data() {
    return {
      data: null,
    };
  },

  components: {
    LeftPoke,
    RightPoke,
  },
};
</script>

<template>
  <div class="container">
    <div class="booldex">
      <LeftPoke />

      <RightPoke />
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
