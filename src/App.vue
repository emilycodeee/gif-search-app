<template>
  <Search @fetchSearch="handleDisplay" />
  <GifList :gifs="gifs" />
</template>

<script>
import Search from "./components/Search.vue";
import GifList from "./components/GifList.vue";

export default {
  name: "App",
  data() {
    return {
      gifs: [],
    };
  },
  methods: {
    handleDisplay(data) {
      this.gifs = data;
    },
  },
  components: {
    Search,
    GifList,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  padding: 50px;
}
</style>
