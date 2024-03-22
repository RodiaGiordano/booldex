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
      },
      deep: true,
    },
  },
};
</script>

<template>
  <div class="right">
    <div class="description">
      <h2>My pokemons</h2>
      <div class="list">
        <ul>
          <li v-for="ele in capturedList">{{ ele }}</li>
        </ul>
      </div>
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
    padding: 40px 0 0 20px;

    .list {
      max-height: 85%;

      overflow-y: auto;
    }

    h2 {
      font-size: 1.8rem;
      height: 15%;
    }
    li {
      line-height: 1.98rem;
      font-size: 1.5rem;

      &::first-letter {
        text-transform: uppercase;
      }
    }
  }
}
</style>
