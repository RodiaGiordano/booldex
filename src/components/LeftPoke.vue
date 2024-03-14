<script>
import ImgPoke from "./partials/ImgPoke.vue";
import StatPoke from "./partials/StatPoke.vue";
import axios from "axios";

export default {
  data() {
    return {
      base_url: "https://pokeapi.co/api/v2/pokemon/",
      uri: "",
      sprite: [
        "https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Pok%C3%A9_Ball_icon.svg/640px-Pok%C3%A9_Ball_icon.svg.png",
      ],

      pokeStats: null,
      defaultSprite: [
        "https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Pok%C3%A9_Ball_icon.svg/640px-Pok%C3%A9_Ball_icon.svg.png",
      ],
    };
  },

  components: {
    ImgPoke,
    StatPoke,
  },

  methods: {
    fetchData() {
      this.uri = this.uri.toLowerCase().trim();
      axios
        .get(`${this.base_url}${this.uri}`)
        .then(({ data: { name, types, height, weight, stats, sprites } }) => {
          this.pokeStats = { name, height, weight, types, stats };

          this.sprite = [sprites.front_default, sprites.back_default];
        })
        .catch(() => {
          this.sprite = [this.defaultSprite];
          this.uri = "";
          if (this.pokeStats) {
            for (let key in this.pokeStats) {
              this.pokeStats[key] = null;
            }
          }
        });
    },
  },
};
</script>

<template>
  <div class="left">
    <div class="search">
      <input
        v-model="uri"
        type="text"
        placeholder="Cerca il nome del Pokemon"
      />

      <font-awesome-icon
        @click="fetchData()"
        :icon="['fas', 'magnifying-glass']"
        class="icon"
      />

      <button class="catch">Catch it!</button>
    </div>
    <div class="pok img">
      <ImgPoke :sprites="sprite" />
    </div>
    <div class="pok descript">
      <StatPoke :stats="pokeStats" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use "../assets/variables.scss" as *;
@use "../assets/mixin.scss";
.left {
  @include mixin.border(true, $bd-primary);
  padding: 20px 50px;
  height: 100%;

  .search,
  .pok {
    margin: 0 auto 10px auto;
  }

  .search {
    height: 30px;

    display: flex;
    align-items: center;
  }

  .search > .icon,
  .catch {
    border: 1px solid black;
    background-color: $bg-secondary;
    &:hover {
      cursor: pointer;
    }
  }
  .search * {
    padding: 5px;
  }

  .search > .catch {
    margin-left: auto;
    font-weight: bold;
  }

  input {
    font-weight: bold;
  }

  .pok.img {
    height: 30%;
    width: 80%;
    border: 25px solid #a7a6a8;

    background-color: $bg-secondary;
  }

  .pok.descript {
    height: 60%;
    background-color: #2cd40d;
    border: 3px solid black;
    border-radius: 10px;
  }
}
</style>
