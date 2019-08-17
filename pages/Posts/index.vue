<template>
  <div>
    <SearchPosts v-on:search-text="searchText"/>
    <Post v-for="post in posts" :key="post.name" :id="post.name" :post="post.url"/>
  </div>
</template>

<script>
import axios from "axios";
import Post from "../../components/Post";
import SearchPosts from "../../components/SearchPosts";

export default {
  components: {
    Post,
    SearchPosts
  },
  data() {
    return {
      posts: []
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };

    try {
      const res = await axios.get("https://api.oceandrivers.com:443/v1.0/getWebCams", config);

      this.posts = res.data.results;
    } catch (err) {
      console.log(err);
    }
  },
  methods: {
    async searchText(text) {
      const config = {
        headers: {
          Accept: "application/json"
        }
      };

      try {
        const res = await axios.get(
          `https://api.oceandrivers.com:443/v1.0/getAemetStation/aeropuertopalma/lastdata?term=${text}`,
          config
        );

        this.posts = res.data.results;
      } catch (err) {
        console.log(err);
      }
    }
  },
  head() {
    return {
      title: "Reddit posts",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Reddit posts"
        }
      ]
    };
  }
};
</script>

<style>
</style>
