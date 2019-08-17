<template>
  <div>
    <nuxt-link to="/posts">Back To Posts</nuxt-link>
    <h2>{{ post }}</h2>
    <hr>
    <small>Post Name: {{ $route.params.name }}</small>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      post: {}
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };

    try {
      const res = await axios.get(
        `https://api.oceandrivers.com:443/v1.0/getAemetStation/aeropuertopalma/lastdata/?test=${this.$route.params.id}`,
        config
      );

      this.post = res.data.post;
    } catch (err) {
      console.log(err);
    }
  },
  head() {
    return {
      title: this.post,
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Reddit post"
        }
      ]
    };
  }
};
</script>

<style>
</style>
