<template>
  <div id="app">
    <ImageUploader />
  </div>
</template>

<script>
import ImageUploader from "./components/ImageUploader";

export default {
  name: "App",
  components: {
    ImageUploader,
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
