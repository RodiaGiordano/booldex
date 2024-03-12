<script>
import ImgPoke from "./partials/ImgPoke.vue";
import StatPoke from "./partials/StatPoke.vue";

export default {
  data() {
    return {};
  },

  components: {
    ImgPoke,
    StatPoke,
  },
};
</script>

<template>
  <div class="show">
    <div class="search">
      <input type="text" value="ciao" /><font-awesome-icon
        :icon="['fas', 'magnifying-glass']"
        class="icon"
      />
      <button class="catch">Catch it!</button>
    </div>
    <div class="pok img">
      <ImgPoke />
    </div>
    <div class="pok descript">
      <StatPoke />
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use "../assets/variables.scss" as *;
.show {
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
  }
  .search * {
    padding: 5px;
  }

  .search > .catch {
    margin-left: auto;
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

.debug {
  border: 1px dashed white;
  min-width: 200px;
  min-height: 100px;
}
</style>
