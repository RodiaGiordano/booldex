<script>
import InnerBoolDex from "./components/InnerBoolDex.vue";

export default {
  data() {
    return {
      title: "Hello world",
    };
  },

  components: {
    InnerBoolDex,
  },
};
</script>

<template>
  <div class="container">
    <div class="booldex">
      <InnerBoolDex />
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use "./assets/variables.scss" as *;

.container {
  display: flex;
  justify-content: center;
  align-items: center;

  padding: 50px;

  .booldex {
    border: 10px solid $bd-primary;

    border-radius: 40px;

    min-height: 80vh;
    min-width: 80vw;
  }
}
</style>
