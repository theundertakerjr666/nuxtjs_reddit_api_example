<template>
  <div>
    <h1>About NuxtJS Reddit example posts</h1>
    <p>Displays results from the API call</p>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "About The App",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Displays results from the API call"
        }
      ]
    };
  }
};
</script>

<style>
</style>
