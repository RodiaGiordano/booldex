<script>
export default {
  data() {
    return {};
  },

  // components: {
  //   ImgPoke,
  // },
};
</script>

<template>
  <div class="show">
    <div class="description debug">ciao</div>
  </div>
</template>

<style lang="scss" scoped>
@use "../assets/variables.scss" as *;
.show {
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
