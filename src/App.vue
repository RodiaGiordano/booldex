<script>
// import MyComponent from "./components/MyComponent.vue";

export default {
  data() {
    return {
      title: "Hello world",
    };
  },

  // components: {
  //   MyComponent,
  // },
};
</script>

<template>
  <div class="container">
    <div class="pokedex"></div>
  </div>
</template>

<style lang="scss" scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;

  padding: 50px;

  .pokedex {
    border: 10px solid #8b0001;
    border-radius: 40px;

    min-height: 80vh;
    min-width: 80vw;
  }
}
</style>
