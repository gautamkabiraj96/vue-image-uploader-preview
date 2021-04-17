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
  text-align: center;
  margin-top: 20px;
}
</style>
