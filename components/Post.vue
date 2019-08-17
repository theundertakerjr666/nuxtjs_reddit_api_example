<template>
  <nuxt-link :to="'posts/' + id">
    <div class="post">
      <p>{{ post }}</p>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  name: "Post",
  props: ["post", "url"]
};
</script>

<style>
.joke {
  padding: 1rem;
  border: 1px dotted #ccc;
  margin: 1rem 0;
}
</style>
