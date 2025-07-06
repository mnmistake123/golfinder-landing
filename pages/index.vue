<script setup>
import pageData from "@/data/index.json";
const page = ref(pageData);

definePageMeta({
  layout: "default",
});
defineProps(["title", "description", "image", "imageAlt"]);
</script>

<template>
  <Container>
    <Hero
      :title="page.hero.title"
      :description="page.hero.description"
      :image="page.hero.image"
      :imageAlt="page.hero.imageAlt"
    ></Hero>
    <Logos :title="page.logos.title" :icons="page.logos.icons"></Logos>
    <Testimonials
      :title="page.testimonials.title"
      :description="page.testimonials.description"
      :items="page.testimonials.items"
    ></Testimonials>
  </Container>
</template>

<style scoped>
.hero-image {
  width: 100%; /* Adjust width as needed */
  max-width: 800px; /* Increase max width */
  height: auto; /* Maintain aspect ratio */
}
</style>
