<template>
  <div class="col-sm">
    <div class="jumbotron" v-for="post in getPosts" :key="post.id">
      <h1 class="display-4 text-center">{{ post.title.rendered }}</h1>
      <div v-if="typeof post._embedded['wp:featuredmedia'] !== 'undefined'">
        <img
          class="img-fluid img-thumbnail mx-auto d-block"
          v-bind:src="post._embedded['wp:featuredmedia'][0].source_url"
        />
      </div>

      <div v-else>
        <div class="alert alert-danger imagenotfound mx-auto d-block" role="alert">
          Image not found for: <b>{{ post.title.rendered }} </b>
        </div>
      </div>

      <div v-html="post.excerpt.rendered" class="text-justify excerpt"></div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    getPosts: Array,
  },
};
</script>

<style scoped>
img {
  width: 80%;
  height: 100%;
}
.excerpt {
  margin: 20px;
}
.imagenotfound{
width: 30%;
}
</style>
