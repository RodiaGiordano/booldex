<script>
import ImgPoke from "./partials/ImgPoke.vue";
import StatPoke from "./partials/StatPoke.vue";
import InputUser from "./partials/InputUser.vue";
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
      capturedList: [],
      pokeShow: null,
    };
  },

  components: {
    ImgPoke,
    StatPoke,
    InputUser,
  },
  props: { captured: [Array, "captured"] },
  emits: ["saveToggle"],

  watch: {
    captured: {
      handler(newVal) {
        this.capturedList = newVal;
      },
      deep: true,
    },
  },

  methods: {
    fetchData() {
      this.uri = this.uri.toLowerCase().trim();
      axios
        .get(`${this.base_url}${this.uri}`)
        .then(({ data: { name, types, height, weight, stats, sprites } }) => {
          this.pokeStats = { name, height, weight, types, stats };

          this.sprite = [sprites.front_default, sprites.back_default];

          this.pokeShow = name;
        })
        .catch(() => {
          this.sprite = [this.defaultSprite];
          this.uri = "";
          this.pokeShow = null;
          if (this.pokeStats) {
            for (let key in this.pokeStats) {
              this.pokeStats[key] = null;
            }
          }
        });
    },

    search(data) {
      this.uri = data;
      this.fetchData();
    },

    saveToggle() {
      if (this.pokeStats.name != null) {
        this.$emit("saveToggle", this.pokeStats);
      }
    },
    cancel() {
      localStorage.clear();
    },
  },
};
</script>

<template>
  <div class="left">
    <InputUser
      @search="search"
      @saveToggle="saveToggle()"
      :captured="capturedList"
      :pokeShow="pokeShow"
    />
    <div class="pok img">
      <ImgPoke :sprites="sprite" />
    </div>
    <div class="pok descript">
      <StatPoke :stats="pokeStats" />
    </div>
    <button @click="cancel()">cancella</button>
  </div>
</template>

<style lang="scss" scoped>
@use "../assets/variables.scss" as *;
@use "../assets/mixin.scss";
.left {
  @include mixin.border(true, $bd-primary);
  padding: 20px 50px;
  height: 100%;

  .pok {
    margin: 0 auto 10px auto;

    &.img {
      height: 30%;
      width: 80%;
      border: 25px solid #a7a6a8;

      background-color: $bg-secondary;
    }
    &.descript {
      height: 60%;
      background-color: #2cd40d;
      border: 3px solid black;
      border-radius: 10px;
    }
  }
}
</style>
