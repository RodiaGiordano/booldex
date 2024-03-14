<script>
// import MyComponent from "./components/MyComponent.vue";

export default {
  data() {
    return {
      details: {
        name: null,
        types: null,
        height: null,
        weight: null,
      },
      attributes: null,
    };
  },

  // components: {
  //   MyComponent,
  // },
  props: {
    stats: [Object, null],
  },

  // watch: {
  //   stats(newVal) {
  //     console.log(newVal);
  //     this.details = { newVal: { name, types, height, weight } };
  //     console.log(this.details);
  //   },
  // },
};
</script>

<template>
  <div class="details">
    <ul>
      <li><strong>ciao:</strong> come stai</li>
      <li><strong>ciao:</strong> come stai</li>
      <li><strong>ciao:</strong> come stai</li>
      <li><strong>ciao:</strong> come stai</li>
    </ul>
  </div>
  <div class="attributes">
    <h2>Stats</h2>
    <ul>
      <li><strong>greve:</strong> come va</li>
      <li><strong>greve:</strong> come va</li>
      <li><strong>greve:</strong> come va</li>
      <li><strong>greve:</strong> come va</li>
    </ul>
  </div>
</template>

<style lang="scss" scoped></style>
