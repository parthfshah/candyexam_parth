<template>
  <div>
    <!-- show contact form -->
    <Nav />
    <Home />
    <h2 class="text-center">Contact Us</h2>

    <contact-form />
  </div>
</template>

<script>
import ContactForm from "../components/utils/ContactForm.vue";
import Nav from "../components/utils/Nav.vue";
import Home from "../components/Home.vue";

export default {
  name: "contact",
  layout: "exam",
  components: {
    ContactForm,
    Nav,
    Home,
  },
};
</script>
