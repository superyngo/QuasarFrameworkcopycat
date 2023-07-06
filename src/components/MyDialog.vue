<script>
export default {
  props: {modelValue: Boolean},
};
</script>

<template>
  <div class="container" v-if="modelValue">
    <div class="shadow"></div>
    <div class="windows"><slot></slot></div>
  </div>
</template>

<style scoped>
.container {
  position: absolute;
  inset: 0;
  display: grid;
  place-content: center;
}
.container:before {
  content: "";
  position: absolute;
  inset: 0;
  background-color: rgb(192, 218, 253);
  opacity: 0.5;
  filter: brightness(0.5);
  z-index: 0;
}
.windows {
  padding: 1rem;
  background-color: #fff;
  max-width: 500px;
  border-radius: 4px;
  z-index: 1;
}
.windows > * {
  margin: 0.5rem;
}
</style>
