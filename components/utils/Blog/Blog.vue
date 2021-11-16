<template>
  <div class="container">
    <h2 class="text-center">Latest Posts <span class="badge bg-success">{{ totalPosts }}</span></h2>
    <!-- Display posts from cms here -->
    <div class="row" v-if="posts != null">
      <Posts :getPosts="posts"> </Posts>
    </div>
    <div v-else>Loading</div>
  </div>
</template>

<script>
import axios from "axios";
import Posts from './Posts.vue';

export default {
  name: "BlogList",
  components: {
    Posts,
  },
  data() {
    return {
      posts: null,
      isLoaded: false,
      totalPosts: null,
    };
  },
  created() {
    axios
      .get("https://exam.candy-dev.com/wp-json/wp/v2/posts?_embed")
      .then((response) => {
        const data = response.data;
        this.totalPosts = data.length;
        const posts = [];
        for (let key in data) {
          const post = data[key];
          posts.push(post);
        }
        console.log("Fetched posts: ", posts);
        this.posts = posts;
        this.isLoaded = true;
      })
      .catch((error) => console.log(error));
  },
};
</script>
