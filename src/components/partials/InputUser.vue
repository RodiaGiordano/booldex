<script>
export default {
  data() {
    return {
      uri: "",
    };
  },
  emits: ["search", "savePoke"],
};
</script>

<template>
  <div class="search">
    <input v-model="uri" type="text" placeholder="Cerca il nome del Pokemon" />

    <font-awesome-icon
      @click="$emit('search', this.uri)"
      :icon="['fas', 'magnifying-glass']"
      class="icon"
    />

    <button @click="$emit('savePoke')" class="catch">Catch it!</button>
  </div>
</template>

<style lang="scss" scoped>
@use "../../assets/variables.scss" as *;
.search {
  margin: 0 auto 10px auto;
  height: 30px;
  display: flex;
  align-items: center;

  > * {
    padding: 5px;
  }

  .icon,
  .catch {
    border: 1px solid black;
    background-color: $bg-secondary;
    &:hover {
      cursor: pointer;
    }
  }
  .catch {
    margin-left: auto;
    font-weight: bold;
  }

  input {
    font-weight: bold;
  }
}
</style>
