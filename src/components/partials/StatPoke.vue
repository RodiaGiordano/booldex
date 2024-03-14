<script>
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

  watch: {
    stats: {
      handler(newVal) {
        console.log(newVal);
        if (newVal.name) {
          const { name, types, height, weight, stats } = newVal;
          this.details = { name, height, weight };
          this.details.types = types[0].type.name;
          this.details.height += " ''";
          this.details.weight += " lbs.";
          this.attributes = [...stats];
        } else {
          this.details.name = null;
          this.attributes = null;
        }
      },
      deep: true,
    },
  },
};
</script>

<template>
  <div v-if="details.name" class="stats">
    <div class="details">
      <ul>
        <li><strong>Name: </strong>{{ this.details.name }}</li>
        <li><strong>Type: </strong>{{ this.details.types }}</li>
        <li><strong>Height: </strong>{{ this.details.height }}</li>
        <li><strong>weight: </strong>{{ this.details.weight }}</li>
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
  </div>
  <div v-else class="noResult">nessun Pokemon selezionato</div>
</template>

<style lang="scss" scoped></style>
