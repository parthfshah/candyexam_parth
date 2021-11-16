<template>
  <nav class="text-center">
    <NuxtLink to="/">
      <button type="button" class="btn btn-lg btn-dark box">Home</button>
    </NuxtLink>

    <NuxtLink to="/contact">
      <button type="button" class="btn btn-lg btn-dark box">Contact Us</button>
    </NuxtLink>
      <br/>
      <br/>

  </nav>


</template>

<style scoped>
.box {
  width: 300px;
  height: 50px;
  margin-right: 20px;
  margin-top: 20px;
}
a {
  text-decoration: none;
  color: white !important;
}
</style>
