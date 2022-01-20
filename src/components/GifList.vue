<template>
  <div id="gifList">
    <Gif v-for="gif in gifs" :key="gif.id" :gif="gif" />
  </div>
</template>

<script>
import Gif from "./Gif.vue";
export default {
  name: "GifList",
  components: { Gif },
  props: ["gifs"],
};
</script>

<style scoped>
#gifList {
  margin-top: 20px;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}
</style>