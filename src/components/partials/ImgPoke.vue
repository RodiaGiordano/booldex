<script>
// import MyComponent from "./components/MyComponent.vue";

export default {
  data() {
    return {
      // pokImg: null,
    };
  },

  // components: {
  //   MyComponent,
  // },

  props: ["sprites"],

  computed: {
    screenImg() {
      if (typeof this.sprites === "string") return this.sprites;
    },
  },
};
</script>

<template>
  <div class="wrapper">
    <img :src="screenImg" alt="" />
  </div>
</template>

<style lang="scss" scoped>
@use "../../assets/variables.scss" as *;

.wrapper {
  border: 5px solid black;
  border-radius: 5px;
  height: 100%;
  text-align: center;

  img {
    height: 100%;
  }
}
</style>
