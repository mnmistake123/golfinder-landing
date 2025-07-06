<!-- <script setup>
import pageData from "@/data/index.json";
const page = ref(pageData);

definePageMeta({
  layout: "default",
});
</script> -->

<!-- <template>
  <Container>
    <Hero
      :title="page.hero.title"
      :description="page.hero.description"
      :image="page.hero.image"
      :imageAlt="page.hero.imageAlt"
      :buttons="page.hero.buttons"
    ></Hero>
    <Logos :title="page.logos.title" :icons="page.logos.icons"></Logos>
    <Features
      :title="page.features.title"
      :description="page.features.description"
      :items="page.features.items"
    ></Features>
    <Testimonials
      :title="page.testimonials.title"
      :description="page.testimonials.description"
      :items="page.testimonials.items"
    ></Testimonials>
    <Cta
      :title="page.cta.title"
      :description="page.cta.description"
      :buttons="page.cta.buttons"
    ></Cta>
  </Container>
</template> -->

<script>
export default {
  data() {
    return {
      deepLink: "", // The deep link will be dynamically set
    };
  },
  mounted() {
    // Get the query parameter from the URL
    const urlParams = new URLSearchParams(window.location.search);
    const id = urlParams.get("id"); // Extract the 'id' query parameter

    if (id) {
      // Construct the deep link dynamically
      this.deepLink = `golfinder.deep.com://details/${id}`;

      // Redirect to the deep link
      window.location.href = this.deepLink;

      // Optional: Add a fallback timeout to redirect to a web fallback URL
      setTimeout(() => {
        window.location.href = "fascinating-bubblegum-fcc5e4.netlify.app"; // Replace with your fallback URL
      }, 500); // Redirect to fallback after 0.5 seconds if the app doesn't open
    } else {
      console.error("No 'id' query parameter found in the URL.");
    }
  },
};
</script>

<template>
  <div>
    <p>
      If you are not redirected automatically,
      <a :href="deepLink">click here</a>.
    </p>
  </div>
</template>

<style>
/* Add any custom styles here */
</style>
