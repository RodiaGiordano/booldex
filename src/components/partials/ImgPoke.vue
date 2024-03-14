<script>
export default {
  data() {
    return {
      spritesInterval: null,
      sprite: null,
      spriteFront: true,
    };
  },

  created() {
    this.sprite = this.sprites;
  },

  props: ["sprites"],

  watch: {
    sprites(newVal) {
      clearInterval(this.spritesInterval);
      this.spriteFront = true;
      if (newVal.length > 1) {
        this.spritesCarosel();
      }
      this.sprite = newVal;
    },
  },

  methods: {
    spritesCarosel() {
      this.spritesInterval = setInterval(() => {
        this.spriteFront = this.spriteFront ? false : true;
      }, 1000);
    },
  },
};
</script>

<template>
  <div class="wrapper">
    <img :src="spriteFront ? sprite[0] : sprite[1]" alt="" />
  </div>
</template>

<style lang="scss" scoped>
@use "../../assets/variables.scss" as *;

.wrapper {
  border: 5px solid black;

  height: 100%;
  text-align: center;

  img {
    height: 100%;
  }
}
</style>
