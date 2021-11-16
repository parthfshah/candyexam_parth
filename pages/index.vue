<template>
  <div class="container">
    <!-- Display posts from cms here -->
    <Nav />
    <Home />
    <Blog />
  </div>
</template>

<script>
import Blog from "~/components/utils/Blog/Blog.vue";
import Nav from "../components/utils/Nav.vue";
import Home from "../components/Home.vue";

export default {
  layout: 'exam',
  components: {
    Blog,
    Nav,
    Home,
  },
};
</script>
