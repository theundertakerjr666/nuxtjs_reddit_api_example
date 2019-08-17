<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="text" placeholder="Search Posts...">
    <input type="submit" value="Search Posts">
  </form>
</template>

<script>
export default {
  name: "SearchPosts",
  data() {
    return {
      text: ""
    };
  },
  methods: {
    onSubmit() {
      this.$emit("search-text", this.text);
      this.text = "";
    }
  }
};
</script>

<style>
</style>
