<template>
  <input
    type="text"
    placeholder="Type something to search for awesome gifs"
    @input="handleInput"
    v-model="search"
  />
  <div v-if="error">
    {{ error }}
  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      search: "",
      error: "",
      timeout: null,
      fatchUrl: `https://api.giphy.com/v1/gifs/random?api_key=0Kbw93SpMVw9pYQMhrE2KVYSmwu7CoqZ&limit=40`,
    };
  },

  methods: {
    async handleSearch() {
      try {
        const res = await fetch(
          `https://api.giphy.com/v1/gifs/search?api_key=0Kbw93SpMVw9pYQMhrE2KVYSmwu7CoqZ&q=${this.search}&limit=40`
        );
        if (!res.ok) throw Error("Something wrong");
        const data = await res.json();
        const result = data.data;
        this.$emit("fetchSearch", result);
      } catch (err) {
        this.error = err.message;
      }
    },
    handleInput() {
      clearTimeout(this.timeout);
      this.timeout = setTimeout(() => {
        this.handleSearch();
      }, 500);
    },
  },
};
</script>

<style scoped>
input {
  padding: 10px 16px;
  border-radius: 4px;
  font-size: 18px;
  outline: 0;
  border: 2px solid #5f5f5f;
  width: 100%;
}

input:focus {
  border-color: #0078e0;
}
</style>