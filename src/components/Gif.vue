<template>
  <div
    class="gif"
    :style="`background-image: url('${gif.images.fixed_width.url}')`"
  >
    <input
      ref="url"
      type="text"
      :value="gif.images.fixed_width.url"
      readonly
      style="flex: 1"
    />
    <button @click="handleCopy">Copy</button>
  </div>
</template>

<script>
export default {
  name: "Gif",
  props: ["gif"],
  methods: {
    handleCopy() {
      this.$refs.url.select();
      document.execCommand("copy");
      alert("Copied!!!");
    },
  },
};
</script>

<style>
.gif {
  width: 240px;
  height: 240px;
  margin-bottom: 20px;
  display: inline-flex;
  justify-content: center;
  align-items: flex-end;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  align-items: flex-end;
}
</style>