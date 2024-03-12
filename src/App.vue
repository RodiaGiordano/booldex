<script>
// import InnerBoolDex from "./components/InnerBoolDex.vue";
import LeftPoke from "./components/LeftPoke.vue";
import RightPoke from "./components/RightPoke.vue";

export default {
  data() {
    return {};
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
      <div class="left">
        <LeftPoke />
      </div>
      <div class="right">
        <RightPoke />
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use "./assets/variables.scss" as *;
@use "./assets/mixin.scss";

.container {
  display: flex;
  justify-content: center;
  align-items: center;

  padding: 50px;

  .booldex {
    border: 10px solid $bd-primary;
    border-radius: 40px;
    height: 800px;
    width: 1100px;
    display: grid;
    grid-template-columns: 50% auto;

    .left {
      @include mixin.border(true, $bd-primary);
    }
    .right {
      @include mixin.border(false, $bd-primary);
    }
  }
}
</style>
