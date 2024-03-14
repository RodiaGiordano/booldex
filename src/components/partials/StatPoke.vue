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

  props: {
    stats: [Object, null],
  },

  watch: {
    stats: {
      handler(newVal) {
        if (newVal.name) {
          const { name, types, height, weight, stats } = newVal;
          this.details = { name, height, weight, types: types[0].type.name };
          this.attributes = [...stats];
          console.log(...stats);
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
  <div v-if="details.name" class="info">
    <div class="details">
      <ul>
        <li><strong>Name: </strong>{{ this.details.name }}</li>
        <li><strong>Type: </strong>{{ this.details.types }}</li>
        <li><strong>Height: </strong>{{ this.details.height }}''</li>
        <li><strong>weight: </strong>{{ this.details.weight }} lbs.</li>
      </ul>
    </div>
    <div class="attributes">
      <h3>Stats</h3>
      <ul>
        <li class="stat" v-for="attribute in attributes">
          <strong>{{ attribute.stat.name }}</strong>
          <div class="bar">
            <div
              class="charge-bar"
              :style="{ width: attribute.base_stat + 'px' }"
            ></div>
          </div>
        </li>
      </ul>
    </div>
  </div>
  <div v-else class="noResult">Nessun Pokemon selezionato</div>
</template>

<style lang="scss" scoped>
.noResult,
.info {
  padding: 15px;
  font-size: 1.1rem;
  font-weight: bold;
}

.info {
  display: flex;
  flex-direction: column;
  gap: 15px;
  line-height: 1.6;

  .attributes {
    li {
      display: flex;
      align-items: center;
      .bar {
        display: inline-block;
        border: 1px solid black;
        border-radius: 5px;
        width: 200px;
        height: 10px;
        margin-left: auto;

        .charge-bar {
          height: 100%;
          background-color: black;
          border-radius: 5px;
        }
      }
    }
  }
}
</style>
