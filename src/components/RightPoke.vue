<script>
export default {
  data() {
    return {
      capturedList: [],
    };
  },

  props: { captured: [Array, "capturedList"] },

  watch: {
    captured: {
      handler(newVal) {
        this.capturedList = newVal;
        console.log("array in right");
      },
      deep: true,
    },
  },
};
</script>

<template>
  <div class="right">
    <div class="description debug">
      <h2>I miei pokemon</h2>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use "../assets/variables.scss" as *;
@use "../assets/mixin.scss";
.right {
  @include mixin.border(false, $bd-primary);
  height: 100%;
  padding: 60px;

  .description {
    height: 100%;
    border: 5px solid $bd-primary;
    background-color: $bg-secondary;
    padding: 10px;
  }
}
</style>
