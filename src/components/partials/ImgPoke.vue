<script>
// import MyComponent from "./components/MyComponent.vue";

export default {
  data() {
    return {};
  },

  // components: {
  //   MyComponent,
  // },
};
</script>

<template>
  <div class="wrapper"></div>
</template>

<style lang="scss" scoped>
@use "../../assets/variables.scss" as *;

.wrapper {
  border: 5px solid black;
  border-radius: 5px;
  height: 100%;
}
</style>
